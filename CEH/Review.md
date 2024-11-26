# Quá trình xác thực, check quyền trên Linux của 1 user
1. Đầu tiên BIOS và UEFI sẽ chịu trách nghiệm load bootloader. Sau đó bootloader sẽ load kernel <br>
vào memory.

2. Tùy thuộc vào configuration của system thì user sẽ đc cho 2 loại đó là: TTY Login (Text based) nghĩa là <br>
mik phải đăng nhập thông qua 1 cái terminal và GUI Login: user sẽ đc cấp 1 giao diện để login như ở trong ubuntu <br>
   ặc kali.

3. Khi user nhập username và password, system sẽ check trong 2 file /etc/passwd và /etc/shadow <br>
```/etc/passwd``` : gồm basic information về username, uid, gid, home directory...<br>
```/etc/shadow```: gồm encrypted password (đã đc hash), password expiration...
   ường thì linux sẽ dùng framwork PAM để làm công việc này

File passwd:

![image](https://github.com/user-attachments/assets/ff21e64f-4c7a-4005-8557-35a05cb4646c)

structure of file passwd:

```
username:password:UID:GID:GECOS:home_directory:shell
```

File shadow: 

![image](https://github.com/user-attachments/assets/db5b65d0-f76e-4b83-9f17-630d827721a4)

structure of file shadow:

```
username:password:lastchg:min:max:warn:inactive:expire:reserved
```

*password*: '!' -> bị locked, '*' -> bị disabled
*lastchg*: number of days that the pass has changed since 1/1/1970 (Unix epoch)
*min*: Sau từng này ngày thì ms đổi đc password
*max*: Sau từng này ngày thì phải đổi pass


4. Sau khi đăng nhập thành công, system sẽ load các environment variable, user's shell (bash, zsh) <br>
running các script: .bashrc, .profile. Ngoài ra nếu graphical login đc sử dụng thì sẽ load GNOME, KDE...

5. Log đăng nhập sẽ được luawu ở /var/log

![image](https://github.com/user-attachments/assets/897d0258-ffda-42ea-a0a4-33aa063154f7)

# Qúa trình authentication và authorization khi lập trình

Sau khi authentication như đã đề cập ở trên, mik sẽ tiến vào bước authorization khi lập trình <br>

1. Checking user roles / permissions
Sau khi authentication xong thì mik sẽ có đc user roles và permission mấy cái này đc stored trong database hoặc 1 ACL (Access Control List)

2. Compare the required permissions
System sẽ check action đối với user đó, action có thể là: edit, view, excute...

4. Allow or Deny access
5. Logging and Auditing
ọi thứ cần được log lại cho audit để xem hoạt động của user

Example:
```
# Simulate user roles and permissions
users = {
    "admin": {"password": "admin123", "role": "admin"},
    "editor": {"password": "editor123", "role": "editor"},
    "viewer": {"password": "viewer123", "role": "viewer"}
}

permissions = {
    "admin": ["edit", "delete", "view"],
    "editor": ["edit", "view"],
    "viewer": ["view"]
}

def check_authorization(user_role, action):
    # Check if the user role has the required permission for the action
    if action in permissions.get(user_role, []):
        return True
    else:
        return False

def authenticate(username, password):
    # Authenticate the user
    user = users.get(username)
    if user and user["password"] == password:
        return user["role"]
    return None

# Example usage
username = input("Enter username: ")
password = input("Enter password: ")

role = authenticate(username, password)
if role:
    print(f"Authentication successful. Your role: {role}")
    action = input("Enter action (edit/delete/view): ")
    
    if check_authorization(role, action):
        print(f"Authorization successful for {action}.")
    else:
        print(f"Permission denied for {action}.")
else:
    print("Authentication failed.")

```
