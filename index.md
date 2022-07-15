# **SSH (Secure Shell)**
  Một giao thức mạng cung cấp cho người dùng (đặc biệt là các QTV mạng) cách truy cập an toàn vào một máy tính qua một mạng không được bảo mật. Bên cạnh đó, SSH cũng cung cấp nhiều bộ tiện ích để triển khai giao thức SSH. Secure Shell là một giao thức cung cấp khả năng xác thực password mạnh mẽ, cùng với khả năng giao tiếp dữ liệu được mã hóa giữa hai máy tính kết nối với nhau qua một mạng mở như Internet. Bên cạnh đó, SSH cũng được sử dụng phổ biến bởi các QTV mạng để quản lý hệ thống và ứng dụng từ xa. Từ đó cho phép đăng nhập vào các máy tính khác qua mạng và thực hiện các tác vụ cơ bản như thực thi lệnh, di chuyển file,…
  
![image](https://user-images.githubusercontent.com/46096038/179175896-80e86cba-0b49-4af1-a7a1-cf7e435f39ee.png)
 
 ## Chức năng chính
Giao thức đảm nhiệm khá nhiều chức năng trong hệ thống điều khiển, liên kết máy chủ. Các chức năng cơ bản phải kể đến như:
- Hỗ trợ truy cập từ xa vào những hệ thống, thiết bị ứng dụng giao thức SSH.
- Cho phép dịch chuyển file an toàn.
- Thực thi lệnh bảo mật, an toàn trên hệ thống điều khiển từ xa.
- Quản lý an toàn và hiệu quả thành phần hạ tầng mạng.
SSH có thể kết hợp với Terminal Session thay thế cho những chương trình Telnet có tính bảo mật thấp.

## Kỹ thuật mã hóa trong SSH
1. Mã hóa Symmetric Encryption
  Mã hóa ứng dụng Secret Key theo hai chiều, giải mã tin cho Host và Client => bất kỳ ai sở hữu mã khóa đều có khả năng giải mã tin nhắn trong quá trình truyền tin.
  
  ![image](https://user-images.githubusercontent.com/46096038/179172706-c2b9d995-aadb-4831-8b04-59e8b704e741.png)
  
  Được ứng dụng để mã hóa hoàn toàn phiên giao dịch diễn ra trong giao thức SSH. 
  Trong đó, Host và Client có nhiệm vụ tạo Key bí mật, tuyệt đối không để lộ cho bên thứ ba.
  * Secret Token chỉ có thời hạn sử dụng trong một phiên SSH, nó hình thành từ chứng thực Client. Khi tạo mới Key, toàn bộ Packets giữa hai máy cần trải qua mã hóa bởi Private Key. Quá trình này gồm cả bước cung cấp mật khẩu bởi người dùng.
3. Mã hóa Asymmetric Encryption
  Dùng 2 khóa riêng biệt để phục vụ mã hóa và giải mã. Bao gồm khóa công khai Public Key và khóa riêng tư Private Key (Cặp khóa public-private key pair)
  
  ![image](https://user-images.githubusercontent.com/46096038/179173085-f41106ca-b953-4b9a-b429-96f930452ce4.png)
  
  Không thể mã hóa tất cả SSH. Nó chỉ có thể sử dụng khi trao đổi thuật toán khóa. Trước thời điểm bắt đầu một phiên, phía 2 đầu trao đổi cần đồng ý khởi tạo cặp khóa Public – Private trong ngắn hạn. Đồng thời, chia sẻ Private Key để tạo ra một Secret Key chung.
5. Mã hóa Hashing
  Không sử dụng vào mục đích giải mã. Chúng hình thành sau mỗi lần nhập liệu, không thể khai thác. Như vậy, Hashing sẽ không thể quay lại để giải mã.
  
  ![image](https://user-images.githubusercontent.com/46096038/179173415-a4325432-ae6a-4d0e-91c9-53e08caea2d2.png)
  
  Client đang giữ Input đó => chỉ Client có thể tạo một crypto-graphic hash để tiến hành xác định hai bên nhập Input.
  
## Điều kiện và cách thức sử dụng SSH
Để sử dụng kết nối SSH, bạn phải được cung cấp một dịch vụ SSH từ máy Remote (từ xa, server), sau đó ở máy Client (local) sử dụng các chương trình SSH Client để kết nối đến máy remote và thực hiện các tác vụ tùy nhu cầu.

Máy chủ dịch vụ SSH là máy tại đó chạy một SSH Server, nó cung cập dịch vụ kết nối SSH đến nó, thông qua xác thực tài khoản user/pass hoặc xác thực bằng public/private key. Nếu đã được cung cấp tài khoản kết nối đến SSH Server, bạn chỉ việc sử dụng các Client SSH phù hợp để kết nối Nếu muốn cài đặt và cấu hình một máy chủ SSH Server thì có thể sử dụng OpenSSH cho các máy chủ Linux hoặc phiên bản cho Windows tại OpenSSH - Windows

SSH Client là các chương trình chạy ở máy trạm (local) có chức năng kết nối đến SSH Server. Bản thân OpenSSH cũng là Client để kết nối - nên ở máy trạm ta sẽ tập trung vào sử dụng OpenSSH Client để thực hành, ngoài ra còn nhiều SSH Client khác, như Putty chạy trên Windows. Khi kết nối có thể tùy cấu hình từ OpenSSH Server có thể xác thực bằng cách nhập username/password hoặc bằng cặp file public/private key.

Đối với Windows cũng đã hỗ trợ OpenSSH như là một gói phân phối cùng hệ điều hành, thông tin của Microsoft nó tích hợp sẵn trong Windows (từ năm 2018 - hoặc có thể cài thêm), điều này giúp cho việc sử dụng ngay SSH trên Windows 10, hoặc Server 2018 về sau mà không phải cài đặt thêm gì.

=> Hoạt động như thế nào: 
  + Nếu đang sử dụng Linux hoặc Mac, sử dụng SSH rất đơn giản. 
  + Nếu sử dụng Windows,cần sử dụng những SSH client để mở kết nối SSH ( trình SSH client phổ biến là Putty,..)
Đối với người dùng xài MAC và Linux, hãy mở terminal và làm theo hướng dẫn sau:
Lệnh SSH có 3 phần:
```
ssh {user}@{host}
```
- {user} : đại diện cho tài khoản người dùng bạn muốn dùng để truy cập.
- {host} : đại diện cho máy tính bạn muốn dùng để truy cập(có thể là địa chỉ IP hoặc tên miền).

 * Khi bạn nhấn enter, nó sẽ hỏi bạn nhập mật khẩu tương ứng cho tài khoản. Khi bạn gõ, bạn sẽ không thấy bất kỳ dấu hiệu nào trên màn hình, nhưng nếu bạn gõ đúng mật khẩu và nhấn enter, bạn sẽ vào được hệ thống và nhận thông báo đăng nhập thành công.
 
 ##Cấu hình máy chủ SSH trên Ubuntu
 
**Bước 1**: Cài đặt các pakage bắt buộc
Cài đặt SSH Server được cung cấp bởi component openssh-server từ OpenSSH
```
sudo apt-get install openssh-server
```
![image](https://user-images.githubusercontent.com/46096038/179177860-281cc872-157d-4038-84e5-91541283b998.png)
<br/>
**Bước 2:** Kiểm tra trạng thái của server <br/>
Khi quá trình tải xuống và cài đặt gói hoàn tất, dịch vụ SSH sẽ chạy, nhưng để chắc chắn, chúng ta cần kiểm tra trạng thái nó bằng
```
service ssh status
```
![image](https://user-images.githubusercontent.com/46096038/179178335-a1960d2c-f310-4848-af51-637c6ecd1cfb.png)

hoặc
```
sudo systemctl status ssh
```
![image](https://user-images.githubusercontent.com/46096038/179179428-b882b64b-b0cf-4501-98bc-c7158db2c80b.png)

Trường **Active** : active(running)
Nếu dịch không chạy, phải kích hoạt bằng lệnh sau
```
sudo systemctl enable --now ssh
```
 **Bước 3**: Cho phép SSH thông qua tường lửa (firewall)
 Ubuntu đi kèm với một công cụ cấu hình tường lửa được gọi là UFW. Nếu tường lửa được bật trên hệ thống của bạn, hãy đảm bảo rằng bạn đã mở cổng SSH
 ```
 sudo ufw allow ssh
 ```
 ![image](https://user-images.githubusercontent.com/46096038/179181726-00971177-8a1a-4f5b-a4c9-47d7d9a615c5.png)
 
 Bây giờ bạn có thể kết nối với hệ thống Ubuntu của mình thông qua SSH từ bất kỳ máy từ xa nào. 
**Bước 4**: Kết nối với máy chủ SSH
Để kết nối với máy chủ Ubuntu của bạn qua mạng LAN, hãy gọi lệnh ssh và theo sau là tên người dùng và địa chỉ IP ở định dạng sau.
```
ssh username@ip_address
```
**Đăng nhập vào máy từ xa bằng cách chạy ssh lệnh sau**
```
ssh vietnetwork@10.0.2.15
```
Khi bạn kết nối lần đầu tiên, bạn sẽ thấy một thông báo như sau

![image](https://user-images.githubusercontent.com/46096038/179183449-82ddbb7a-a499-49c6-805e-b144228df0ff.png)
<br/>
Nhập yes và bạn sẽ được nhắc nhập mật khẩu của mình.

![image](https://user-images.githubusercontent.com/46096038/179183534-ddfce994-79b6-4d85-ab65-16b92e5c45e5.png)
<br/>
Sau khi nhập mật khẩu

![image](https://user-images.githubusercontent.com/46096038/179183772-d9a21240-5da0-4eee-8f73-d64ea558c192.png)
<br/>
**Kết nối với SSH sau NAT.**
```
ssh username@public_ip_address
```
**Tắt SSH trên Ubuntu**
```
sudo systemctl disable --now ssh
```
**Sau đó để kích hoạt lại nó, hãy nhập:**
```
sudo systemctl enable --now ssh
```
