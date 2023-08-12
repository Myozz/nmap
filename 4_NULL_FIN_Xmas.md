**NULL, FIN và Xmas TCP port scan ít được sử dụng hơn với 3 cái trước. Có mối liên kết với nhau, và có xu hướng "ẩn" hơn SYN**
# NULL: nmap -sN ...
* NULL sẽ gửi request không flag, mục tiêu sẽ phản hồi lại bằng RST nều port đóng

----------------------

# FIN: nmap -sF ...
* Thay vì gửi packet rỗng như NULL, FIN sẽ gửi request với flag FIN, vẫn là phản hồi RST nếu đóng

----------------------

# Xmas: nmap -sX ...
* Xmas sẽ gửi gói tin TCP "dị dạng" (malformed) và nhận RST nếu port đóng
