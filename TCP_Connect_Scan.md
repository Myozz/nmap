nmap -sT ...
------------
*Về three-way handshake (bắt tay 3 bước):
  Đầu tiên máy truyền tin sẽ gửi TCP request tới server với flag SYN. Server sẽ nhận gói tin này với một TCP response gồm SYN cũng như ACK flag. Cuối cùng server sẽ     phản hồi lại bằng cách gửi một TCP request với ACK flag
------------
TCP Connect Scan hoạt động dựa trên three-way handshake với mỗi port. Nói cách khác, nmap sẽ connect tới mỗi TCP port và xác định server đang mở dựa vào tín hiệu nhận được
Nếu nmap gửi một TCP request với SYN flag tới một port đóng thì server sẽ phản hồi với một TCP packet với RST (Reset) flag. Như vậy nmap có thể nhận diện port mở hay đóng dựa vào flag nhận được là RST hay ACK
