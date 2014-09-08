_Happiness is like a kiss. You must share it to enjoy it._

# Một số lệnh cơ bản thường dùng 

_Đây là các lệnh thường dùng khi thao tác với linux server (chủ yếu là RHEL, CentOS)_

## Thao tac vs git

_Gồm các lệnh liên quan tới login vào remote server, copy file, folder_

| Nội dung | Chi tiết  | Ví dụ | Chú ý |
| -------- | -------- |--------|---|
| Xem nội dung folder   | `ls`    |`ls`  | xem dưới chân mình là ai|
| Xem mình đang ở đâu   | `pwd`     |`pwd`   | xem mình đang ở đâu trong server|
| Copy file    | `cp file_nguon file_dich`     |`cp README.txt README_copy.txt`    | |
| Copy folder    | `cp -r folder_nguon folder_dich`     |`cp -r  public_html public_html_copy`    | public_html_copy là folder được tạo mới |
| Backup file/folder    | `cp  file{,.20140101}`     |`cp   KISSME.txt{,.20140101}`    | file `KISSME.txt.20140101` sẽ được tạo ra cùng thư mục với KISSME.txt|
| Đổi tên file/folder    | `mv file_nguon file_dich`  |`mv README.txt KISSME.txt` |KISSME.txt là tên file mới|
| Xoá file/folder     | `rm ten_file`  | `rm README.txt` |Trước khi xoá cần cân nhắc backup. Với folder, thêm tham số `-r`: `rm -r folder`.  |
| Xem dung lượng file/folder| `du -sh`|`du -sh filename` hoặc `du -sh *`|Xem dung lượng đĩa là `df -h`|
| Nén file/folder | `zip -r ten_file_zip ten_folder_can_zip` | `zip -r hellozip hello` | Lệnh có thể dùng nhiều CPU, tránh dùng khi nhiều user| 
| Tạo link mềm (soft link) | `ln -s folder_nguon folder_dich` |  `ln -s /tmp/hello /tmp/byebye ` | folder nguồn và đích nên là đường dẫn tuyệt đối. /tmp/byebye là folder sẽ được tạo mới |
| Recursively Delete .svn Directories | `find . -type d -name .svn -exec rm -rf {} \; ` |  | The `{}` references the file being acted upon by `-exec` and `\;` terminates the exec command |
## Tạo mới/ghi/đọc file

_Gồm các lệnh liên quan tới thao tác file_

| Nội dung | Chi tiết  | Ví dụ | Chú ý |
| -------- | -------- |--------|---|
| Tạo file mới rỗng   | `touch` ten_file   | `touch README.md` | đảm bảo user có quyền ghi|
| Tạo file mới và ghi nội dung  | `vi` ten_file   | `vi KISSME.md` | `vi` là trình editor mặc định thường gặp trên Linux|
| Thoát `vi`  | Nhấn `ESC`, rồi `:q`, sau đó `ENTER`     |  | |
| Thoát `vi` và không lưu thay đổi | Nhấn `ESC :q!`    |  | `q` = quit|
| Thoát `vi` và lưu thay đổi | Nhấn `ESC :wq`    |  | `w` = write, `q` = quit|
| Xem file từng phần 1 | Dùng lệnh `less`  | `less README.md` | Nhấn `ESC :q` để thoát. Nhấn `keydown` để xem tiếp |
| Xem file | Dùng lệnh `tail`  | `tail README.md` | `tail` có nghĩa là `cái đuôi`, cho phép xem file từ cuối lên |
| Xem toàn bộ file | Dùng lệnh `cat` | `cat KISSME.md` | Toàn bộ nội dung file sẽ được in ra |
| Xem file log| Dùng lệnh `tail -f`  | `tail -f README.md` | Xem file dưới dạng streaming, hiện nội dung ngay khi có input |
| Thêm nội dung vào file | Dùng lệnh `cat` | `cat fileA >> fileB` | Nối nội dung file A vào file B |




## MySQL
| Nội dung | Chi tiết  | Ví dụ | Chú ý |
| -------- | -------- |--------|---|
| Login vào MySQL   | `mysql -uusername -ppassword`  | `mysql -ucusack2RO -pegbdf5s`|Nếu mà trường hợp pass có 1 số ký tự đặc biệt VD: `cap3&MeG3p4G` thi không cần nhập pass luôn chỉ cần để `-p` sau đó nhập pass khi nhận được yêu cầu |
| Import MySQL   | `mysql -uusername -ppassword ten_database < filename`   |`mysql -ucusack2RO -pegbdf5s avada < myNewDB.sql` ||
| Dump (export) MySQL   | `mysqldump -uusername -ppassword ten_database > filename`  |`mysqldump -ucusack2RO -pegbdf5s avada > myNewDB.sql` |Dùng để backup DB|
| Login vào MySQL trên 1 host khác    | `mysql -uusername -ppassword -hhost_address`  | `mysql -ucusack2RO -pegbdf5s -hgoooogle.com` |-h nghĩa là chỉ định host |
| List tất cả DB    | `show databases;` | | Thực hiện sau khi đăng nhập |
| Tạo DB mới     | `create database ten_DB;` | `create database helloworld;`| Thực hiện sau khi đăng nhập |
| Sử dụng 1 DB     | `use  ten_DB;` | `use  helloworld;`| Thực hiện sau khi đăng nhập |
| List tất cả bảng    | `show tables;` | `show tables;`| Thực hiện sau khi `use database` |
| Xem cấu trúc bảng    | `describe  ten_bang;` | `describe hello_table;`| Thực hiện sau khi `use database` |
