nmap -sT ...
------------
*Về three-way handshake (bắt tay 3 bước):
  Đầu tiên máy truyền tin sẽ gửi TCP request tới server với flag SYN. Server sẽ nhận gói tin này với một TCP response gồm SYN cũng như ACK flag. Cuối cùng server sẽ    phản hồi lại bằng cách gửi một TCP request với ACK flag
  
  ![image](https://github.com/Myozz/nmap/assets/94811005/9d995125-143f-42a8-b2bc-9e8693bcaace)


*TCP Connect Scan hoạt động dựa trên three-way handshake với mỗi port. Nói cách khác, nmap sẽ connect tới mỗi TCP port và xác định server đang mở dựa vào tín hiệu nhận được

*Nếu nmap gửi một TCP request với SYN flag tới một port đóng thì server sẽ phản hồi với một TCP packet với RST (Reset) flag. Như vậy nmap có thể nhận diện port mở hay đóng dựa vào flag nhận được là RST hay SYN/ACK

  ![image](https://github.com/Myozz/nmap/assets/94811005/15de4cd9-abb9-4be9-8529-e49102ff5238)

*Nếu port mở nhưng lại được bảo vệ bởi tường lửa thì sao? Nhiều tường lửa được config để drop gói tin nhận được, tức là gửi SYN đi thì không có gì quay trở lại

*Thâm chí có thể config tưởng lửa để response bằng RST, ví dụ:
  
    iptables -I INPUT -p tcp --dport <port> -j REJECT --reject-with tcp-reset

Điều này khiến việc quét mục tiêu trở nên khó khăn hơn
