# Quá trình xác thực, check quyền trên Linux của 1 user
1. Đầu tiên BIOS và UEFI sẽ chịu trách nghiệm load bootloader. Sau đó bootloader sẽ load kernel <br>
vào memory.

2. Tùy thuộc vào configuration của system thì user sẽ đc cho 2 loại đó là: TTY Login (Text based) nghĩa là <br>
mik phải đăng nhập thông qua 1 cái terminal và GUI Login: user sẽ đc cấp 1 giao diện để login như ở trong ubuntu <br>
   ặc kali.

3. Khi user nhập username và password, system sẽ check trong 2 file /etc/passwd và /etc/shadow <br>
```/etc/passwd``` : gồm basic information về username, uid, gid, home directory...<br>
```/etc/shadow```: gồm encrypted password (đã đc hash), password expiration...

File passwd:
![image](https://github.com/user-attachments/assets/ff21e64f-4c7a-4005-8557-35a05cb4646c)

File shadow: 
![image](https://github.com/user-attachments/assets/db5b65d0-f76e-4b83-9f17-630d827721a4)

4. Sau khi đăng nhập thành công, system sẽ load các environment variable, user's shell (bash, zsh) <br>
running các script: .bashrc, .profile. Ngoài ra nếu graphical login đc sử dụng thì sẽ load GNOME, KDE...

5. Log đăng nhập sẽ được luawu ở /var/log
![image](https://github.com/user-attachments/assets/897d0258-ffda-42ea-a0a4-33aa063154f7)
