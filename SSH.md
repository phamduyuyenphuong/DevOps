 Cách kết nối bên trong các server để thực hiện một số bảo trì hoặc hành động
 
 ![image](https://user-images.githubusercontent.com/46096038/198554398-9fc17a8f-077d-4574-a18f-461a4354433e.png)
 
 Putty tương tự với SSH , nếu sử dụng bất kì Windows 
EC2 Instance Connect sử dụng Mac, Linux, Windows tất cả các phiên bản, nhưng hiện tại chỉ hoạt động với Amazon NX2

 1. SSH (Secure Shell) ?
 - Cho phép remote máy từ xa bằng command line
 
 ![image](https://user-images.githubusercontent.com/46096038/198558895-05accb4a-48cb-4bb0-8247-d58cb336bc90.png)
  
  EC2 đang chạy Amazon Linux 2 và có IP công khai, cho phép SSH port 22 tới bất kỳ IP nào

**Cách SSH vào EC2 Instance**
 **Windows**

 2. sử dụng PuTTY để thực hiện SSH (win7, 8,win 10)
  
  Trong trường hợp tệp tải xuống dạng ".PEM", Có thể tạo trực tiếp định dạng PPK từ PuTTYgen
  
![image](https://user-images.githubusercontent.com/46096038/200764583-6aa101d0-87ef-462a-a222-66b6969dbd09.png)

![image](https://user-images.githubusercontent.com/46096038/200764030-0af177e2-13eb-48fa-aa98-de78172d095b.png)
 ![image](https://user-images.githubusercontent.com/46096038/200764104-7e761ef3-82cb-4318-a4f9-6a390a7ce735.png)
 
 - Nhập tên server hoặc địa chỉ IP muốn kết nối
 
 ec2-user@52.194.232.234 địa chỉ IPv4 public (SSH) 
 => open => truy cập trực tiếp vào EC2 Instance
 
3. Win10

 Kiểm tra SSH trên Windows bằng PowerShell hoặc command line
 
 ![image](https://user-images.githubusercontent.com/46096038/200766561-e1747176-3464-441a-9fcf-fd09fb306d8c.png)
 
  => lệnh SSH đã tồn tại
  Nếu không tồn tại,sử dụng PuTTY 
  
![image](https://user-images.githubusercontent.com/46096038/200774431-d92638ae-afc1-47be-ae3f-d874d17a39dd.png)

![image](https://user-images.githubusercontent.com/46096038/200775511-ebc99498-7223-46a5-979c-45386878335e.png)

- Đầu tiên ở thư mục chứa tệp ".PEM"
- security group có port 22 cho SSH
- Có thể thay đổi quyền của thư mục ".PEM" để không hiển thị các cảnh báo
4. Có thể sử dụng EC2 Instances để thay thế SSH

![image](https://user-images.githubusercontent.com/46096038/200791479-b7432f78-4593-45e0-ac3e-458e47980d69.png)

user name: được cung cấp theo mặc định

Không còn tùy chọn khóa SSH, bởi vì khi kết nối đã tải lên khóa SSH tạm thời

=> Connect => truy cập vào Amazon Linux 2 AMI

![image](https://user-images.githubusercontent.com/46096038/200792733-6ff7ab48-69e6-434d-8adc-ee6d5ea78e27.png)

Đảm bảo Inbound rules có mở port 22

![image](https://user-images.githubusercontent.com/46096038/200793944-d844472c-64fd-4de4-b356-683a6feb3f9b.png)

5 **EC2 Instance Roles Demo**

Nguyên tắc chung : Không bao giờ nhập key ID và Secret Access Key vào EC2 instance

Thay vào đó sử dụng IAM roles để cung cấp thông tin đăng nhập

![image](https://user-images.githubusercontent.com/46096038/200798959-5197cf06-686b-4103-b975-b9ddf4889af6.png)

![image](https://user-images.githubusercontent.com/46096038/200800104-b4f723f3-0c01-439e-8173-8b0c6210d078.png)

![image](https://user-images.githubusercontent.com/46096038/200800179-3ab6f3ed-4b27-4cc4-ad8a-609ca62da6a5.png)

![image](https://user-images.githubusercontent.com/46096038/200800345-97ccda4a-25be-48cc-8ec7-c0fb45d6df4d.png)

Sau khi thêm IAM roles DemoRoleForEC2, thực hiện lệnh **aws iam list-users**
![image](https://user-images.githubusercontent.com/46096038/200800787-8278eec5-8725-42ba-9d13-2afddd2bc69d.png)

 
