# nmap -sU ...

* Không như TCP, UDP là dạng không trạng thái (stateless). Thay vì chơi "bắt tay", UDP hoạt động dựa trên việc gửi gói tin tới port mục tiêu và đại khái là hết :)). Có thể hiểu là nó ưu tiên tốc độ kết nối max speed thay vì chất lượng (vd: chia sẻ video). Nhưng do thiếu sự xác nhận nên UDP cũng khó quét hơn và cũng chậm hơn nữa.
  - Khi một gói tin được gửi tới một UDP port đang mở, sẽ không có phản hồi nào. Khi điều này xảy ra, nmap sẽ hiển thị là ```open|filtered```. Như vậy nghĩa là nó cho rằng port đang mở, nhưng được firewall bảo vệ. Nếu mà nhận được UDP response (hiếm), thì sẽ được đánh dấu ```open```. Chủ yếu thì nó sẽ không phản hồi, trong trường hợp gửi request lần hai để double-check, vẫn không có phản hồi nào thì port sẽ được đánh dấu là ```open|filter```
  - Khi gói tin được gửi tới một UDP port đóng, mục tiêu sẽ phản hồi bằng một gói tin ICMP (ping) với một thông báo port không thể truy cập.

------------------------

* Bởi vì việc khó xác dịnh một UDP port có mở hay không, UDP scan chậm vc (khoảng 20 min để scan 1000 port khi mạng ổn định). Cho nên nếu dùng để luyện tập thì nó nên được đi kèm với ```--top-ports <number>```, nó sẽ quét top ```<number>``` những port phổ biến nhất.

------------------------

Khi UDP Scan, nmap thường gửi các request rỗng. Cho thấy rằng, với những port của các dịch vụ phổ biến, nó sẽ gửi các payload dành riêng nhằm tạo ra phản hồi, thu được kết quả chính xác hơn
