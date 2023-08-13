* Ta đã được thấy những kĩ thuật vượt tưởng lửa (NULL, FIN, Xmas scan). Tuy nhiên, có một firewall config phổ biến mà ta bắt buộc phải biết để bypass tưởng lửa

* Default firewall của Windows sẽ block mọi ICMP packets. Điều này dẫn tới một vấn đề: Không chỉ chúng ta sử dụng ping để kiểm tra host trước khi triển khai các hành động trên mục tiêu, nmap cũng vậy. Nghĩa là nmap sẽ bỏ qua host này và coi như nó là dead host

* Vậy nên ta cần sử dụng một option ```-Pn```, nó sẽ báo với nmap rằng đừng để ý đến việc ping host trước khi scan. Có nghĩa là nmap sẽ luôn coi như host đang alive, khiến block ICMP trở nên vô dụng. Tuy nhiên, nó tốn khá nhiều thời gian để scan (nếu host thực sự dead thì nó vẫn cứ scan)

* Nếu ta đang ở trên mạng cục bộ, nmap cũng có thể dùng ARP request để xác định trạng thái host

----------------------

* Có một loạt các công cụ khác để Nmap có thể qua mặt tường lửa. Ta sẽ không đi sâu vào chúng, tuy nhiên có một số chú ý sau:
  - ```-f``` dùng để chia nhỏ packets, khiến nó không giống một packet nữa và có thể đi qua tưởng lửa hoặc IDS
  - Vẫn là dùng ```-f``` nhưng cung cấp nhiều quyền kiểm soát hơn size cho gói tin ```-mtu <number>```, chấp nhận đơn vị truyền tin lớn để gửi tin. **Phải** là bội của 8
  - ```--scan-delay <time>ms```: được dùng để delay thời điểm gửi tin. Nó rất hữu dụng nếu mạng không ổn định, nhưng lại có thể luồn quả được tường lửa, IDS dựa trên thời gian được áp dụng
  - ```--badsum```: Tự động cung cấp những checksum (tổng kiểm) không hợp lệ của gói tin. Bất cứ TCP/IP stack thật nào đều sẽ drop packet này, tuy nhiên tưởng lửa có lẽ sẽ phản hồi chúng tự động phản hồi mà không check cái checksum đấy. Như vậy, cách này có thể dùng để xác định sự hiện diện của tường lửa/IDS
  
