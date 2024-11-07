
### 1. **Cơ bản về Linux**  
   - **Hệ điều hành Linux là gì**: Nắm các khái niệm cơ bản về Linux như kernel, shell, hệ thống file, và sự khác biệt giữa Linux và các hệ điều hành khác (Windows, macOS).
   - **Linux distributions (bản phân phối Linux)**: Tìm hiểu các bản phân phối phổ biến (Ubuntu, CentOS, Debian, Red Hat), ưu và nhược điểm của chúng trong môi trường doanh nghiệp.

### 2. **Lệnh Linux Cơ Bản**  
   - **Điều hướng file và thư mục**: Các lệnh `cd`, `ls`, `pwd`, `mkdir`, `rmdir`, `cp`, `mv`, `rm`, và `find`.
   - **Quyền truy cập file**: Lệnh `chmod`, `chown`, `chgrp` để thay đổi quyền và sở hữu file. Hiểu rõ các chế độ quyền (read, write, execute).
   - **Nén và giải nén file**: Sử dụng `tar`, `zip`, `gzip`, `bzip2` để nén và giải nén dữ liệu.
   - **Hiển thị nội dung file**: `cat`, `head`, `tail`, `more`, `less` để xem nội dung file. `grep` để tìm kiếm chuỗi trong file.
   - **Xử lý văn bản**: `sed`, `awk` để chỉnh sửa và phân tích văn bản trong file.

### 3. **Quản lý Tiến Trình (Process Management)**  
   - **Kiểm tra tiến trình**: Lệnh `ps`, `top`, `htop` để kiểm tra các tiến trình đang chạy.
   - **Quản lý tiến trình**: Lệnh `kill`, `pkill`, `killall` để dừng các tiến trình. Hiểu về các tín hiệu của `kill` như `SIGTERM`, `SIGKILL`.
   - **Tác vụ nền và ưu tiên tiến trình**: Lệnh `bg`, `fg` để chuyển tiến trình giữa nền và foreground. `nice` và `renice` để thay đổi mức ưu tiên.

### 4. **Quản lý Gói Phần Mềm**  
   - **Công cụ quản lý gói**: `apt` (Debian/Ubuntu), `yum` (CentOS/RHEL), `dnf` (Fedora), và cách dùng các lệnh cơ bản như `install`, `update`, `remove`.
   - **Docker**: Hiểu về cách cài đặt Docker, chạy container, và quản lý Docker images trên Linux.

### 5. **Quản Lý Người Dùng và Quyền Hạn**  
   - **Tài khoản người dùng**: Tạo, xóa, và sửa tài khoản người dùng với `useradd`, `userdel`, `usermod`.
   - **Nhóm (Groups)**: Tạo và quản lý các nhóm người dùng bằng `groupadd`, `groupdel`, và `groupmod`.
   - **Quyền truy cập và quản lý root**: Hiểu cách sử dụng `sudo` và tài khoản root để thực hiện các tác vụ có quyền cao.

### 6. **Hệ Thống File**  
   - **Cấu trúc thư mục Linux**: Biết các thư mục quan trọng như `/home`, `/etc`, `/var`, `/bin`, `/usr`, `/tmp`, `/root`.
   - **Mount và unmount hệ thống file**: Sử dụng `mount` và `umount` để gắn kết và gỡ hệ thống file.
   - **Kiểm tra dung lượng đĩa và giám sát file hệ thống**: Lệnh `df`, `du` để kiểm tra dung lượng đĩa và `fsck` để kiểm tra lỗi trên hệ thống file.

### 7. **Quản lý Mạng**  
   - **Các lệnh mạng cơ bản**: `ifconfig`, `ip`, `ping`, `netstat`, `traceroute`, `nslookup` để kiểm tra và quản lý mạng.
   - **Kết nối SSH**: Sử dụng `ssh` để kết nối từ xa, `scp` và `rsync` để truyền file giữa các hệ thống.
   - **Firewall**: Sử dụng `ufw` (trên Ubuntu) hoặc `firewalld` để quản lý firewall.

### 8. **Cron Jobs và Automation**  
   - **Tác vụ định kỳ với cron**: Thiết lập và quản lý cron jobs với `crontab`, hiểu cú pháp `crontab` và các trường của nó để lên lịch thực hiện các tác vụ tự động.
   - **Systemd và quản lý dịch vụ**: Sử dụng `systemctl` để quản lý các dịch vụ và daemon chạy ngầm.

### 9. **Shell Scripting**  
   - **Các khái niệm cơ bản về shell scripting**: Biết cách viết script với `#!/bin/bash`, hiểu các cú pháp điều kiện (if-else), vòng lặp (for, while), và các biến trong shell script.
   - **Tự động hóa với scripts**: Viết script để tự động hóa các tác vụ thường xuyên, sử dụng lệnh `echo`, `read`, `exit`, và các lệnh kiểm tra như `[[ ]]`.

### 10. **Giám sát và Log**  
   - **Các file log trong Linux**: Hiểu cấu trúc các file log quan trọng như `/var/log/syslog`, `/var/log/messages`, `/var/log/auth.log`.
   - **Kiểm tra và phân tích log**: Sử dụng `tail -f` để xem log theo thời gian thực, và `grep` để tìm kiếm trong log.

### 11. **Bảo mật Hệ Thống**  
   - **Cấu hình SSH**: Cấu hình file `/etc/ssh/sshd_config` để bảo mật kết nối SSH, bao gồm thay đổi port mặc định, tắt đăng nhập root.
   - **Quản lý firewall**: Sử dụng `ufw` hoặc `iptables` để thiết lập các luật firewall.
   - **Cấp quyền và bảo mật file**: Hiểu về các quyền của file, cách sử dụng `chmod`, `chown`, `setuid`, `setgid`, và `sticky bit` để bảo vệ các file quan trọng.

### 12. **Làm việc với Docker trên Linux**  
   - **Cài đặt và sử dụng Docker**: Cách cài đặt Docker, các lệnh cơ bản để tạo, chạy, và quản lý container (`docker run`, `docker ps`, `docker stop`, `docker rm`, `docker images`, `docker rmi`).
   - **Docker Compose**: Sử dụng Docker Compose để quản lý nhiều container với file `docker-compose.yml`.
   - **Quản lý dữ liệu trong container**: Hiểu về volumes và bind mounts để lưu trữ dữ liệu.

### 13. **Quản Lý Tài Nguyên Hệ Thống**  
   - **Theo dõi hiệu suất**: Sử dụng các lệnh `top`, `htop`, `vmstat`, `free` để theo dõi tài nguyên hệ thống (CPU, RAM, disk I/O).
   - **Giám sát dung lượng ổ đĩa và RAM**: `df -h`, `free -m` để xem dung lượng ổ đĩa và bộ nhớ khả dụng.
   - **Kết hợp với Airflow và MongoDB**: Quản lý tài nguyên khi chạy các công việc nặng trên Airflow và MongoDB.
