# Install DVWA on Ubuntu
[Kali](https://www.youtube.com/watch?v=GmWQ1VIjd2U&list=PLHUKi1UlEgOJLPSFZaFKMoexpM6qhOb4Q&ab_channel=CryptoCat)
[Ubuntu](https://www.youtube.com/watch?v=kMUdmmTL7OM&ab_channel=gp_sec)
> Install PHP & Apache2 & mysql
> www-data user

# XSS Reflected
## What?
Lợi dụng client request từ server, server sẽ respond lại thì lúc này hacker sẽ trả về respond chứa mã độc bao gồm <br>
user request.

## How?
### Low level
![image](https://github.com/user-attachments/assets/fdf93f3b-71f3-4570-be23-e80618d17bc5)

*Đầu tiên khi vào OWASP ta sẽ view source php*

> header() in php

1. Redirect to another page. <br>
```php
<?php
header("Location: https://www.example.com");  
exit; // Prevent further code execution 
?>
```
Nó sẽ gửi  request 'chuyển tiếp' đến server. Yêu cầu server phải đưa cho nó cái link trên. Dùng exit để đảm bảo ko <br>
có câu lệnh nào chèn thêm. <br>
2. Tránh caching
  
```php
<?php
header("Cache-Control: no-cache, must-revalidate");
header("Expires: Sat, 26 Jul 1997 05:00:00 GMT");
?>  
```
> Caching là gì?

Lưu lại những cái hoạt động thường xuyên của user để tăng tốc độ truy cập web. Cải thiện performance, giảm load on <br>
backend sys, database...

Ví dụ ở trên cho ta biết đó là loại Browser-caching, nó sẽ gia hạn cho resources được phép tồn tại bao lâu. Ngoài ra, <br>
mik còn 1 số loại caching như: Server side caching, CDN caching, Application Level caching... Bên cạnh đó đi kèm đó chính là <br>
những stragegy để caching (sẽ tìm hiểu sau)

3.  


