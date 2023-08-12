nmap -sS ...
--------------
*SYN scan được dùng để scan mục tiêu, khác TCP Connect Scan ở chỗ nó scan ở dạng ẩn (steal) hoặc half-open :||
  TCP Connect Scan thực hiện một quá trình 3-way handshake đầy đủ, còn SYN sẽ phản hồi RST sau khi nhận được SYN/ACK từ server thay vì ACK (điều này ngăn chặn server    liên tục request 
![image](https://github.com/Myozz/nmap/assets/94811005/b3ee2a22-4db6-46ca-890d-27d3b49da510)

*Lợi ích
  +/ Bypass hệ thống phát hiện xâm nhậm (Intrusion Detection) CŨ
  
  +/ SYN scan thường không bị log lại bởi litsening port
  
  +/ Nhanh hơn TCP Connect Scan

*Bất lợi:
  
  +/ Yêu cầu sudo perm để hoạt động bởi vì nó yêu cầu quyền tạo raw packéts 
  
  +/ Những service không ổn dịnh có thể bị sập khi SYN scan

SYN scan sẽ được mặc định khi scan trên nmap với quyền sudo, nếu không có sudo thì mặc định sẽ là TCP Con Scan
--------------

*Còn drop khi gặp port đóng hoặc có firewlll thì tương tự TCP Con

