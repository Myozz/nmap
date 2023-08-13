# Overview
* Nmap Scripting Engine (NSE) là một phần bổ sung cực vjp pro 123 cho Nmap, mở rộng chức năng cho Nmap. NSE Scripts được viết bằng lang Lua, và được sử dụng để làm nhiều thứ: từ scan lỗ hổng, rồi tự động khai thác chúng. NSE rất hữu dụng trong trong reconnaisance. Tuy nhiên, thư viên của nó cực kì rộng lớn
* Có rất nhiều chức năng (category), có thể kể đến như:
	- ```safe```: Không ảnh hưởng tới mục tiêu
	- ```intrusive```: Ngược lại với safe
	- ```vuln1```: Quét lỗ hổng
	- ```exploit```: Khai thác lỗ hổng
	- ```auth```: Bypass xác thực để chạy services
	- ```brute```: Bruteforce xác thực để chạy services
	- ```discovery```: Truy vấn cái services đang chạy để lấy thêm thông tin 

-------------------

# Làm việc với NSE
* Kích hoạt NSE bằng ```--script```, sử dụng category (vd: vuln) bằng ```--script=vuln```. 

* Để chạy một script bất kì, dùng ```--script=<script-name>```, VD: ```--script=http-fileupload-ẽploiter```
* Có thể chạy nhiều scripts cùng lúc bằng cách dùng dấu phẩy, VD: ```--script=<scr-name1>, <scr-name2>```
* Một số scripts yêu cầu đối số. Có thể cung cấp đối số bằng ```--script-args```. VD với ```http-put``` script (dùng để upload file bằng phương thức PUT). Nó có 2 đối số: URL upload, và vị trí file trên đĩa, VD:
```nmap -p 80 --script http-put --script-args http-put.url='/dav/shell.php',http-put.file='./shell.php'```
(Các đối số được ngăn cách bởi dấu phẩy)

* Nmap scripts cũng có help menu, sử dụng bằng ```nmap --script-help <scr-name>.

----------------------

# Search Scripts
* Có 2 option cho việc này. Thứ nhất là website nmap.org, website này chứa danh sách tất cả các scripts chính thức (official). Thứ 2 là trong máy của bạn (attacking machine), nmap sẽ đặt chung ở ```/usr/share/nmap/scripts```. Mặc định tất cả NSE scripts đều có ở đấy, đây cũng là nơi mà nmap lấy script khi ta dùng lệnh.
* Có 2 cách để search những scripts được tải xuống. Một là mở file ```/usr/share/nmap/scripts/scripts.db```. Dù vậy, đây không thực sự là một database mà chỉ là một file văn bản chứa filename và category của từng scripts đang có
![image](https://github.com/Myozz/nmap/assets/94811005/1ce4fb96-1ed5-4727-aa7b-90228d043c36)

* Nmap sử dụng file này nhằm theo dõi và sử dụng scripts. Tuy nhiên, ta cũng có thể ```grep``` để tìm scripts, VD:
  
		grep "ftp" /usr/share/nmap/scripts/scripts.db
![image](https://github.com/Myozz/nmap/assets/94811005/70fbb547-79ef-41db-b959-505d12f2b2b1)

* Cách thứ hai là dùng ```ls```. VD, ta có thể lấy kết quả như bên trên của grep như sau:

		ls -l /usr/share/nmap/scripts/*flip*
![image](https://github.com/Myozz/nmap/assets/94811005/ecb1b697-6eef-4db4-b892-9c8f499cece4)
Sử dụng ```*``` hai bên để search

