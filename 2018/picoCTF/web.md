# Web
- Most of the challenges required source inspection, directory guessing, user agent editing, or cookie modification
- One challenge required very basic SQL injection
- [Buttons](http://2018shell2.picoctf.com:18342/) involved monitoring the HTTP response code when a second button was pressed. I used curl to modify the request so it was POST (initially copped as cURL using Chrome dev tools):
```curl 'http://2018shell2.picoctf.com:18342/button2.php' -X POST -H 'Connection: keep-alive' -H 'Upgrade-Insecure-Requests: 1' -H 'DNT: 1' -H 'User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.3497.100 Safari/537.36' -H 'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8' -H 'Referer: http://2018shell2.picoctf.com:18342/button1.php' -H 'Accept-Encoding: gzip, deflate' -H 'Accept-Language: en-GB,en-US;q=0.9,en;q=0.8' -H 'Cookie: password=asdas; username=sadasd; admin=True' --compressed```

## The Vault [250 pts]

- php login
- view the source code to see that there are validation rules for SQLi
- inject `admin'--` into the *username* field and you receive the flag:
→ `picoCTF{w3lc0m3_t0_th3_vau1t_c09f30a0}`
