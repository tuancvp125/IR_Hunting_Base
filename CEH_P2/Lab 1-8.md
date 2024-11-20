# New things
## Hash function
## Aircrack-ng tools
### Actual activities in a wireless network

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

### Discovering network



