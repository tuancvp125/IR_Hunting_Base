# 1

![image](https://github.com/user-attachments/assets/b37daf61-f6d1-4b44-b991-082b466c014d)

Answer:

Số hiệu cổng ứng dụng đích 

# 2

![image](https://github.com/user-attachments/assets/da3cf04c-270f-40d0-b517-65b15b8d30b6)

Answer:

1. 1 Tiến trình chỉ đc sử dụng 1 socket <br>
2. Nút B sẽ ko làm kiểu này vì nó sẽ tốn nhiều tài nguyên và nó cx ko thể bt đc bên A có bao nhiêu tiến trình <br>
ũng ko thể bt lúc nào A gửi thế nên cx ko lập đc socket <br>
3. Chuẩn
4. Sai vì 2 cổng trên A khác nhau
5. Chuẩn (Best Effort - Nhanh nhất có thể)

# 3

![image](https://github.com/user-attachments/assets/0ef30811-35f8-47a0-9b86-a7433365ea8d)

Answer:

1. Cần độ chính xác --> ko thể
2. Kết nối từ xa cần phải đc tin cậy --> ko dùng UDP
3. Đúng --> có thể dùng UDP
4. Đúng --> có thẻ dùng UDP
5. Sai cần độ tin cậy và chính xác

# 4

![image](https://github.com/user-attachments/assets/035fea6b-614c-43d7-b4df-4882ab5e8578)

Answer:

e. Time-out dùng cho cơ chế truyền thông tin cậy (kiểm tra in4 có bị mất hay ko)
f cũng đúng.
![image](https://github.com/user-attachments/assets/90d94175-9f18-44b5-be56-33f3df9a72fb)

# 5

![image](https://github.com/user-attachments/assets/39ad542d-9467-47a0-bc18-fd3800a0d3e8)

Answer:

B. Ko sử dụng báo nhận --> ko tin cậy
C. UDP cũng kiểm tra checksum

# 6

![image](https://github.com/user-attachments/assets/d0dbfcaf-806c-49d9-8d75-c02b9f73f811)

Answer:

![image](https://github.com/user-attachments/assets/4c4bb935-809f-4b89-bfeb-66ec2a223533)

# 7

![image](https://github.com/user-attachments/assets/c4566cec-3def-4e86-bede-7490900046e6)

Answer:

Phương án sai là B,C. UDP sẽ chuyển tiếp gói tin với cổng đích tương ứng lên tầng application vả <br>
Kiểm tra lỗi trên gói tin ở phần header.

![image](https://github.com/user-attachments/assets/eb83d4da-f2c2-4749-bb4d-816dfbc47df4)

# 8

![image](https://github.com/user-attachments/assets/962c7024-48bd-430e-af1c-5da96a0e4e81)

Answer:

![image](https://github.com/user-attachments/assets/d1b2165e-8d0b-43d0-99b1-81aae0c24176)

# 9

![image](https://github.com/user-attachments/assets/12e5a0f9-d7b0-4f19-8b88-8ee7a9eac08e)

Answer:

A. UDP ko bt giao thức ở tầng trên sdung giao thức j --> ko thể gửi lên cho tầng trên sửa lỗi <br>
B. Đúng --> hủy gói tin <br>
D. ko có báo nhận <br>
C. ko gửi lại để sửa. <br>

# 10

![image](https://github.com/user-attachments/assets/899fd204-545b-4fa8-8af5-e37fbede1d3e)

TCP sẽ được gửi lại khi
-  Gói tin bị lỗi
-  3 ACK có giá trị khác nhau đc gửi đến
-  Xảy ra timeout

# 11

![image](https://github.com/user-attachments/assets/97559771-bf3b-4167-9aec-edf25d75edb1)

Answer:

![image](https://github.com/user-attachments/assets/5e22c9fe-18d7-4565-8d76-24572c45a74c)

Thiết lập cờ SYN là để thiết lập liên kết.

# 12

![image](https://github.com/user-attachments/assets/3db3b5af-ea7a-49de-84cb-ad91ba34d052)

Answer:

Swnd : Kích thước dữ liệu tối đa (Bên gửi có thể gửi) <br>
Swnd <= min(Rwnd, Cwnd) <br>
Rwnd : Kích thước cửa sổ nhận --> số kích thước dữ liệu tối đa bên nhận có thể nhận <br>
Cwnd : Kích thước cửa sổ kiểm soát tắt nghẽn <br>

--> Đáp án sẽ là C

# 13

![image](https://github.com/user-attachments/assets/6c8c923e-6f45-47db-a0e4-1bf0d0d08b08)

Answer:

![image](https://github.com/user-attachments/assets/bacbba34-5aee-432f-8b6d-c6f3d304d4ad)

--> Chỉ cần quan tâm đến 16 bit sau là được

Cổng 25 là SMTP

# 14

![image](https://github.com/user-attachments/assets/d34ae765-467b-4117-9c8b-37ef7f48300c)

Answer:

Giá trị checksum để phát hiện lỗi gói tin

# 15

![image](https://github.com/user-attachments/assets/caf7d0a4-6758-42e4-837c-5a69e7c0f696)

Answer:

Trường checksum trong TCP có giá trị 16 bit --> Sử dụng checksum 16 bit

# 16

![image](https://github.com/user-attachments/assets/2565342c-6bd5-4c79-809f-c718c1924d7a)

Answer:

Báo kết thúc gửi liên kết. Ko phải nhận

# 17

![image](https://github.com/user-attachments/assets/bcbfa3d4-d8a6-4e57-bf64-580f00aed500)

Answer:

A. 2 host A & B khi kết nối tới C có thể dùng 1 cổng C để thiết lập 2 liên kết đến 2 host này. <br>
B. Sai. Hoàn toàn có thể sử dụng số hiệu cổng giống nhau <br>
C. Phát hiện xảy ra tắc nghẽn ở 1 bên thì chỉ cần đóng liên kết slow start ở cổng đố <br>
D. Đúng. Sử dụng 2 socket khác nhau để liên kết A và B <br>
E. Giá trị cửa sổ nhận cho biết số byte có thể nhận được tối đa. Mà giá trị này đại diện cho <br>
buffer còn trống

# 18

![image](https://github.com/user-attachments/assets/8a02cd5b-612e-470a-94bb-54a5c0f6bdbe)

Answer:

B. Loại Bỏ gói tin <br>
C. Gửi lại ACK xác nhận các gói tin trước đó --> báo gói tin hiện tại đang bị lỗi <br>

# 19

![image](https://github.com/user-attachments/assets/f863c207-9e74-4fd0-b234-724b142bd079)

Answer:

A. Chính là phát hiện sớm tắc nghẽn <br>
D. Đây là cơ chế pipeline của TCP

![image](https://github.com/user-attachments/assets/fee99e87-ce2f-47f8-9df4-b073f894fec5)

# 20

![image](https://github.com/user-attachments/assets/766c166d-e48c-4203-be0a-12280cdd2cbc)

Answer:

2 giai đoạn: Slow Start và tránh tắc nghẽn

![image](https://github.com/user-attachments/assets/3f032ae5-70c2-45ad-af0f-6f601758e80f)

A. Có thực hiện <br>
B. Có thực hiện (khởi tạo slow start) <br>
C. Kích thước cửa sổ kiểm soát sẽ tăng tuyến tính chứ ko giữ nguyên <br>
D. Có thực hiện

# 21

![image](https://github.com/user-attachments/assets/4b4df280-4bf3-45ef-b581-92ec8577318c)

Answer:

![image](https://github.com/user-attachments/assets/c03f3bab-f115-4fe2-a270-44ada0d36080)

A. Chuẩn, Kích thước cửa sổ kiếm soát sẽ tăng gấp đôi khi gửi thành công trong giai đoạn Slow-Start <br>
B. Giai đoạn tránh tắc nghẽn (Từ slowstart --> timeout) vẫn tăng <br>
C. Sai. Khi có time out phải bắt đầu ở slow-start <br>
D. Khi bắt đầu slow-start, kích thước cửa sổ ks tắc nghẽn là 1ms (đúng) <br>

![image](https://github.com/user-attachments/assets/76e7e92b-91d6-42f3-8d94-ed517a558b9e)

# 22

![image](https://github.com/user-attachments/assets/73a9a50b-943d-4531-8d34-99f329141ff8)

Answer:

Lượt 10 và lượt 23

# 23

![image](https://github.com/user-attachments/assets/9b9e88b8-af7a-4164-824c-f17857e1ddcb)

Answer:

Giai đoạn tránh tắc nghẽn thì cứ tăng tuyến tính mà chọn

Chọn C

# 24

![image](https://github.com/user-attachments/assets/55720ad5-c606-4d1d-8647-c167ba982bca)

Answer:

Slow-start - 1 (9 & 22)

# 25

![image](https://github.com/user-attachments/assets/6d1ea0ab-abd0-4ef6-b2f4-2be455dc1b29)

Answer:

B. Phải hủy gói tin khi gói tin bị lỗi <br>
C. Gửi lại gói tin với ACK = 5600 vì gói tin bị lỗi chứ ko pải là (5600 + 1400) --> đây là <br>
báo nhận gói tin thành công


# 26

![image](https://github.com/user-attachments/assets/d79b0f20-4352-4f19-9e18-104d2fdbfa48)

Answer:

Cứ time out là sẽ quay về với giá trị của cửa sổ kiểm soát tắc nghẽn 1mss( 1400)

# 27

![image](https://github.com/user-attachments/assets/b9b0a6a9-b0f3-4a4e-83eb-cae78e09d479)

Answer:

Khi nhận được 3 ACK thì sẽ xuất hiện hồi phục nhanh, giá trị ngưỡng = 1/2 giá trị 

![image](https://github.com/user-attachments/assets/bbbbe3b0-626f-4010-8ef1-510fb2c53cbd)

# 28

![image](https://github.com/user-attachments/assets/fa9b8860-361a-4390-ad1f-8319d60ef76c)

Answer:

A. Chuẩn, Bên gửi sẽ tính toán lại giá trị của cửa sổ kiếm soát tắc nghẽn <br>
B. Kiếm soát cửa sổ kiểm soát luồng là do bên nhận tính toán <br>
C. Phát lại dữ liệu đã gửi mà chưa nhận đc ACK

# 29

![image](https://github.com/user-attachments/assets/f8fd2913-5103-423c-81cd-4fdae3f3e8b3)

Answer:































