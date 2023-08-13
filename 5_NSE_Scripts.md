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
