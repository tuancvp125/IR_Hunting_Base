# Cấu trúc IP address

## Bit nhận dạng class
![image](https://github.com/user-attachments/assets/24d695ce-898a-4c1e-91f8-9646146bb8a9)

Phần đầu sẽ là bit nhận dạng class. Có 5 class A,B,C,D,E

![image](https://github.com/user-attachments/assets/d851942a-e49f-4000-aff1-2ae103bb9186)

## Phân lớp
![image](https://github.com/user-attachments/assets/3eaed4eb-abfd-4cb3-830a-f998bcc2f5ca)

*Giải thích: Vdu đối với lớp A mik sẽ có 7 bit do 1 bit đầu phân lớp --> Network ID có 128 dc (0-> 127) - 2 địa chỉ = 126 và Host ID sẽ có (32 - 16) <br>
2 ^ 16 - 2 = 65534 địa chỉ.*

> Tại sao lại bỏ 2 địa chỉ toàn bit 0 và toàn bit 1

-  Toàn bộ bit 0: ko có nghĩa
-  Toàn bộ bit = 1: Thông báo nội bộ

