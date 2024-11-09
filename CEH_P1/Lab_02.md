# Thu thập thông tin về website kenh14.vn

## Sử dụng Netcraft
![image](https://github.com/user-attachments/assets/9fffe5d2-48a5-493b-8816-05316ce49278)

> rDNS
- Bình thường thì khi nhập 1 domain name, user sẽ đc trả về IP do DNS look up làm việc, còn rDNS thì ngược lại

*Ở đây sẽ hiển thị những thông tin cơ bản*

![image](https://github.com/user-attachments/assets/80c1ac28-ee71-48e3-a49c-e7bec70bab61)

![image](https://github.com/user-attachments/assets/e88cb11b-78fb-41af-ab28-2bc6618c4696)

*Các công nghệ được sử dụng ở server & client*

## Sử dụng Shodan

*Tra bằng địa chỉ IPv4 lấy từ netcraft*

![image](https://github.com/user-attachments/assets/1e9ab63b-7a37-4458-a98d-a611204e9c22)

## Sử dụng WHO-IS

![image](https://github.com/user-attachments/assets/637f5e26-03ec-4587-97c6-b2d4aa7c4da0)

![image](https://github.com/user-attachments/assets/8e4268cd-947d-42bb-a0c3-760d9e7688d5)

Dựa vào những thông tin ở trên ta có thể thấy:
  - Ngoài những thông tin cơ bản như tên tổ chức, địa chỉ, thông tin của admin website, mik còn bt
    thêm về mnt-by: manage entry for IP range, mnt-lower: manages the lower-level assignments of IP blocks or
    subnets within this range và mnt-route: manages the routing in4 for IP range.
  - Maintainer có vai trò đảm bảo data mà WHOIS ghi nhận là chính xác.
  - Nhưng những thông tin này được cập nhật cũng đã khá lâu (gần nhất là 2022).
  - Cái status **ALLOCATED PORTABLE** nghĩa là: ALLOCATED - dãy IP range đc manage bởi 1 regional org
    trong trường hợp này là APNIC. Còn PORTABLE - dchi này có thể đc truy cập ko giới hạn
  - Phần origin *AS135905* (ASN : Autonomous System Number) mục đích là để những cái network khác có thể
    reach được đến cái subnet này (subnet 14.225.10.0/24). Còn phần chữ và số đại diện cho 1 org (VNPT).

## Sử dụng Ping và Traceroute
> TTL

Số lượng hop mà nó sẽ đi qua. Cứ mỗi hop đi qua thì value TTL sẽ giảm đi 1. TTL giúp packets ko bị loop
  khi truyền trong mạng.

## Sử dụng NMAP

## Kiểm tra host up/down = cách gửi ICMP packet

![image](https://github.com/user-attachments/assets/1c4f371b-f375-40b9-abbf-3b3cbda4ec73)


### Full Open Scan

![image](https://github.com/user-attachments/assets/1619bb80-6641-473a-83b9-e1c86e8bbcc3)

![image](https://github.com/user-attachments/assets/8aa8d572-70fb-4bd9-9925-d4e76494587f)

Quá trình này thực hiện 3-handshake (bắt đầu = SYN, trả về SYN-ACK và kthuc = ACK từ sender) sau khi
hoàn tất sender đóng connection = gửi RST. Đó là trường hợp server nhận connection (trả về SYN-ACK), nếu ko nhận sẽ trả về RST. 

## Hafl-Open Scan

![image](https://github.com/user-attachments/assets/d806fc03-b639-4f28-aa0a-f0890bccc000)

Cách này thì nhanh hơn cách trên vì sau khi kết nối thành công từ server (nhận gói SYN-ACK), nó sẽ gửi RST luôn mà ko gửi ACK xong
RST (đóng connection luôn).


### ACK Probe Scanning

![image](https://github.com/user-attachments/assets/4523c3b8-557b-4862-9627-ae279f8baa40)

Cái này thì cho biết rằng tường lửa nó chặn những port nào. Ở đây thì tất cả các port ko bị chặn nhưng chưa chắc đã được kết nối.
Muốn chi tiết hơn đến phần sau

### Hệ Điều Hành đang chạy

![image](https://github.com/user-attachments/assets/6c20792a-ff13-41d0-abac-5f4829418de2)









