# **Port Forwarding**
## 1.Port Forwarding là gì?
  Một quá trình chuyển tiếp của một port cụ thể từ hệ thống mạng này sang một mạng khác.
  Điều này có phép người dùng bên ngoài có thể dễ dàng truy cập vào mạng nội bộ bên trong thông qua bộ định tuyến đã mở NAT – Network Address Translation.
  ![image](https://user-images.githubusercontent.com/46096038/179646633-7e64f6c0-74fd-46e9-ab98-4ce25690948c.png)
  <br/>
## 2.Port là gì?
Port thực ra là một cổng giúp cho quá trình chuyển tiếp được đơn giản hơn.
Nếu ví địa chỉ IP như một địa chỉ của một tòa nhà nào đó thì cổng Port chính là số nhà của từng căn hộ bên trong.
Khi chúng ta kết nối vào hệ thống internet thì sẽ có rất nhiều đường truyền dữ liệu khác nhau.
Những đường truyền này đều được điều hành một cách chính xác thông qua các cổng port khác nhau.
![image](https://user-images.githubusercontent.com/46096038/179648340-f5b04d32-fec9-4687-a308-69b1116334b0.png)
<br/>
Nếu đang sử dụng DHCP => địa chỉ Ip có thể thay đổi => phải thiết lập lại Port Forwarding ( Cấu hình lại IP tĩnh của máy chủ)
 - Trước khi cấu hình Port Forwarding trên router, cần chuẩn bị :
 + IP nào đang được sử dụng ở thời điểm hiện tại.<br/>
 window: _ipconfig/all_ <br/>
 linux: sudo apt install net-tools -> _sudo ifconfig_
 ## Thiết lập IP tĩnh từ máy chủ 
Bước 1: Mở hộp thoại Command Prompt.<br/>
Bước 2: Thực hiện dòng lệnh ipconfig/all.<br/>
Bước 3: Sau khi hộp thoại được mở ra, hãy ghi lại những thông tin như IPv4 Address, Subnet Mask, DNS Server và Default Gateway, ... <br/>
Sau khi có được những thông tin này, bạn có thể thiết lập địa chỉ IP tĩnh như sau:
![image](https://user-images.githubusercontent.com/46096038/179652435-f09a151a-8ede-4f77-a6a9-971e55a1b5dc.png)
<br/>
Bước 4: Mở hộp thoại Run (Window + R). Nhập dòng lệnh ncpa.cpl để mở Network Connections.<br/>
Bước 5: Nhấn chuột phải vào Ethernet. Chọn Properties.<br/>
Bước 6: Tiếp tục chọn Internet Protocol Version 4 (TCP/IPv4), chọn Properties.<br/>
Bước 7: Nhấp chọn Use the following IP address.<br/>
Bước 8: Nhập tất cả những thông tin bạn đã có được từ hộp thoại Command Prompt trước đó.<br/>
Bước 9: Chọn OK và hoàn tất.<br/>
## Thiết lập IP tĩnh từ Router
Bước 1: Truy cập Router với quyền admin. <br/>
Bước 2: Tìm danh sách các thiết bị được kết nối với Router và địa chỉ IP của chúng. <br/>
Bước 3: Chọn bất kỳ một địa chỉ IP nào từ danh sách, sau đó chọn Add hoặc Reserve. <br/>
## 6 bước cấu hình Port Forwarding
**Bước 1**: Nhập địa chỉ IP Router lên thanh địa chỉ của trình duyệt Web.<br/>
Địa chỉ Ip Router:
- Đối với các máy Windows: Mở Command Prompt, nhập ipconfig/all vào khung Search. Địa chỉ IP chính là dãy số ở mục Default Gateway.
- Đối với Macbook: Sau khi mở Terminal, hãy nhập dòng lệnh netstat -nr
- Đối với Linux: Mở Terminal, gõ Route, bạn sẽ nhận được thông tin mình cần.<br/>
Sau khi có được địa chỉ IP Router, hãy nhập những con số này vào thanh địa chỉ của trình duyệt Web để mở trang cấu hình Router của bạn.
**Bước 2**: Đăng nhập tên và mật khẩu
Sau khi mở trang cấu hình Router, đăng nhập tên và mật khẩu vào (trường hợp đã từng thiết lập các thông tin cá nhân), chưa đăng nhập:
- Gõ “Admin” vào cả 2 phần Username và mật khẩu ở Router Linksys
- Gõ “Admin” vào phần Username và “Password” vào phần mật khẩu ở Router Netgear.
- Đối với các Router khác, có thể bỏ qua phần Username, chỉ cần nhập vào phần mật khẩu “Admin”<br/>
Nếu không nhớ được tất cả thông tin cài đặt này, bạn có thể nhấn nút Reset trên Router, sau đó tìm kiếm thông tin mặc định trên phần cài đặt online.<br/>
**Bước 3**: Tìm kiếm Port Forwarding<br/>
**Bước 4**: Tìm cấu hình có sẵn (DMZ HOST)<br/>
**Bước 5**: Tùy chỉnh mục nếu chương trình bạn muốn thêm không được liệt kê trong danh sách.<br/>
Với mỗi Router khác nhau thì các bước thực hiện thay đổi cũng sẽ khác nhau. Nhưng cơ bản chúng ta có thể thực hiện như sau:<br/>
- Nhập tên chương trình mà bạn muốn thêm vào
- Chọn giao thức cho chương trình đó, đó có thể là TCP, UDP hoặc cả 2.
- Chọn Port mà bạn muốn sử dụng
- Chọn địa chỉ IP nội bộ để gắn Port Forwarding.
 <br/>
**Bước 6**: Nhấn lưu cài đặt <br/>
 <br/>
Bước cuối cùng, để lưu lại tất cả những cài đặt bạn đã thực hiện, hãy nhấn vào mục Apply thay vì bấm Save. Tiến hành khởi động lại Router, bạn sẽ thấy được những khác biệt.
