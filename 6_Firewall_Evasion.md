* Ta đã được thấy những kĩ thuật vượt tưởng lửa (NULL, FIN, Xmas scan). Tuy nhiên, có một firewall config phổ biến mà ta bắt buộc phải biết để bypass tưởng lửa

* Default firewall của Windows sẽ block mọi ICMP packets. Điều này dẫn tới một vấn đề: Không chỉ chúng ta sử dụng ping để kiểm tra host trước khi triển khai các hành động trên mục tiêu, nmap cũng vậy. Nghĩa là nmap sẽ bỏ qua host này và coi như nó là dead host

* Vậy nên ta cần sử dụng một option ```-Pn```, nó sẽ báo với nmap rằng đừng để ý đến việc ping host trước khi scan. Có nghĩa là nmap sẽ luôn coi như host đang alive, khiến block ICMP trở nên vô dụng. Tuy nhiên, nó tốn khá nhiều thời gian để scan (nếu host thực sự dead thì nó vẫn cứ scan)

* Nếu ta đang ở trên mạng cục bộ, nmap cũng có thể dùng ARP request để xác định trạng thái host
