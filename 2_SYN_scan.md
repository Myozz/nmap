nmap -sS ...
--------------
*SYN scan được dùng để scan mục tiêu, khác TCP Connect Scan ở chỗ nó scan ở dạng ẩn (steal) hoặc half-open :||
  TCP Connect Scan thực hiện một quá trình 3-way handshake đầy đủ, còn SYN sẽ phản hồi RST sau khi nhận được SYN/ACK từ server thay vì ACK (điều này ngăn chặn server 
