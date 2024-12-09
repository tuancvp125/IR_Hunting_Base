# Question
## 1
![image](https://github.com/user-attachments/assets/b205530e-c63c-455c-9aa9-f2e840c9a0bd)

*B. Biểu diễn các bit thành tín hiệu là chức năng của tầng vật lý (Physical).*

## 2
![image](https://github.com/user-attachments/assets/3c60921f-1f93-4ecf-8603-e7bfcab84729)

*Hình trục* 

Answer: 
![image](https://github.com/user-attachments/assets/893e34c2-838c-497e-b9b7-339abc2c7e91)

## 3
![image](https://github.com/user-attachments/assets/2a6c388c-10ac-4867-ba03-736dc022ed05)

*Lưu ý: Nếu mạng hình sao mà sử dụng switch, router thì sẽ là point-point còn hub thì đa điểm*

## 4
![image](https://github.com/user-attachments/assets/c1b286e4-a77e-4fb6-9cd5-8140d312b1f1)

Có 3 đáp án

## 5 
![image](https://github.com/user-attachments/assets/93ebba04-ccb1-48b0-8764-1781c4401b06)

Answer:

![image](https://github.com/user-attachments/assets/34bf9c6c-4f9f-4545-aaa7-b4e0ad087aa9)

Bọn này là những multiple access protocol nằm ở data-link layer, còn 1 cái protocol khác đấy là <br>
logical of data link control -> phụ trách việc handling những error... Còn bọn MAP sẽ làm việc khi có<br>
multiple kết nối...

**Random Access Protocol**: được dùng trong wireless LAN <br>
**Control Access Protocol**: Tức là khi 1 trạm chuyển tin thì pải được sự đồng thuận từ tất cả các trạm <br>
**Channelization Protocol**: Khi 1 trạm chuyển tin thì nó có thể access qua tất cả các trạm... <br>

*Đây là cách làm của thầy*

![image](https://github.com/user-attachments/assets/ee5e3e4f-f679-4fce-ba02-41d8653c37fe)

## 6

![image](https://github.com/user-attachments/assets/bf5ec129-08c8-4989-89f0-f6dd216a6585)

Answer:

![image](https://github.com/user-attachments/assets/123e563b-5016-473b-a70a-33a5064412f7)

## 7

![image](https://github.com/user-attachments/assets/be707f9f-7cf1-4550-9a6b-ee451d5c9e7d)

Answer:

![image](https://github.com/user-attachments/assets/0e45f332-17b8-4d03-8f62-ddc842b29063)

## 8

![image](https://github.com/user-attachments/assets/fbfbb358-871a-4753-8155-f4b3b68beee2)


Answer:

![image](https://github.com/user-attachments/assets/4028e9a0-9b30-4fab-9c6a-2a0fa8263900)

> Switch

Cái thằng này ở network layer. Trình tự mà nó gửi data như sau: <br>
Giả sử có 2 PC1 và PC2 đc kết nối cùng 1 switch và PC1 đang muốn truyền data sang cho PC2 <br>

1. Đầu tiên nó sẽ nhận frame data từ PC1, trong đó có chứa MAC của PC1 và MAC của PC2 (des)
2. Nó sẽ có 1 cái bảng MAC của các thiết bị để xem MAC của PC2 có khớp không nếu có thì gửi luôn <br>
òn ko thì nó sẽ flooding (tức là broadcast đến tất cả các máy trừ PC1)
3. Nó có cơ chế tự học nó sẽ biết đc gói tin này từ MAC nào qua MAC nào thông qua port nào <br>
ên nó sẽ ko có protocols nào dẫn đường đi.

> Router

Cái thằng này giống ở bài thực hành số 3 (HANOI & SAIGON). Thằng này thì cần routing table để biết đc <br>
gói tin nó sẽ đi đâu. Frame sẽ chứa địa chỉ IP của src và dst.

Cuối cùng mik có cái bảng này:

![image](https://github.com/user-attachments/assets/657e1c26-927f-433a-83bc-a8c0ef652df2)

## 9

![image](https://github.com/user-attachments/assets/8514b05c-fe0b-41af-b1a3-4d5567c0306b)

Answer:

![image](https://github.com/user-attachments/assets/6115ae11-e795-4bf0-9fac-28c736522149)

## 10

![image](https://github.com/user-attachments/assets/125c8d43-f895-4240-9ae6-abd2cb639c1e)

**Lưu ý:** Cơ chế tự học chỉ sử dụng cho source address ko dùng cho dst address.

## 11

![image](https://github.com/user-attachments/assets/3cbe1639-375a-43dd-a1b3-4eb13bf475ca)


Answer:

![image](https://github.com/user-attachments/assets/143a5ff2-1afc-4177-9fd1-9bb4c556b61f)

Switch có thể tìm lỗi...

## 12

![image](https://github.com/user-attachments/assets/c3e2e7b6-aa5a-4072-bebe-c3818aa67f33)

Answer:
















