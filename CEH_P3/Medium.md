# XSS reflected
Chạy thử alert
```
<script>alert("Pwned")</script>
```
![image](https://github.com/user-attachments/assets/0a96cc6c-5946-4990-8191-0498ad1ce2d3)

*Ko chạy được script*

View source:

![image](https://github.com/user-attachments/assets/336757f8-8fd8-4c24-a22f-07ab56072432)

*Đã thay thế <script> = ''*

## Sol
Cái này nó chỉ check lowercase thôi chứ chưa check uppercase nên script sẽ là 
```
<SCRIPT>alert("Pwned")</script>
```
Kết quả:

![image](https://github.com/user-attachments/assets/5ef81811-20fd-4c42-a1ba-78e1f64e428c)

# XSS Stored

# XSS DOM
View source:

![image](https://github.com/user-attachments/assets/f4507537-b30c-4b23-bc6a-591cac4dd1e5)

```
<?php

// Is there any input?
if ( array_key_exists( "default", $_GET ) && !is_null ($_GET[ 'default' ]) ) {
    $default = $_GET['default'];
    
    # Do not allow script tags
    if (stripos ($default, "<script") !== false) {
        header ("location: ?default=English");
        exit;
    }
}

?>
```

*Không cho excute script ở default tag*

Đầu tiên lấy value của element "default" ở parameter query do GET responsible, sau đó dùng stripos để tìm string <script>. Nếu tìm thấy <br>
lập tức set về mặc định English và exit.

![image](https://github.com/user-attachments/assets/c61d6fb7-eec8-4760-8f41-bd1c329ef01c)
*Kể cả khi dùng <SCRIPT> như lỗi med reflected ở trên hì vẫn ko xi nhê*



