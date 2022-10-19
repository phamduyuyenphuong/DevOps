1.**Amazon EC2 là gì** ? (Elastic Compute Cloud)
- Cách để thực hiện cơ sở hạ tầng như một dịch vụ trên AWS
- Bao gồm nhiều thứ ở cấp độ cao :
 + Thuê các máy ảo trên EC2
 + Lưu trữ dữ liệu trên ổ đĩa ảo hoặc ổ đĩa EBS
 + Phân phối tốc độ load trên các máy (ELB)
 + Mở rộng các dịch vụ bằng cách sử dụng auto-scaling group (ASG)
**1.1 EC2 sizing & configuration options (tùy chọn cấu hình và định cỡ)**
- Operating System(OS) : Linux, Windows hoặc Mac OS
- Có bao nhiêu  power và cores (CPU)
- Có bao nhiêu random-access memory (RAM)
- Có bao nhiêu dung lượng lưu trữ :
 + Network-attached (EBS & EFS) : được gắn qua mạng
 + hardware (EC2 Instance Store)
 - Loại Network: muốn gắn vào là card mạng nhanh hay Public IP address
 - firewall rules : nhóm bảo mật
 - Bootstrap script để định cấu hình phiên bản ở lần khởi chạy đầu tiên: dữ liệu EC2 User
**1.2 EC2 User Data**
• Có thể chuyển hướng đến boostrap của chúng tôi bằng cách sử dụng tập lệnh EC2 user data
• bootstrapping có nghĩa là khởi chạy các lệnh khi máy khởi động
• Tập lệnh đó chỉ được chạy một lần khi bắt đầu phiên bản đầu tiên
• Dữ liệu người dùng EC2 được sử dụng để tự động hóa các tác vụ khởi động như:
+ Cài đặt bản cập nhật
+ Cài đặt phần mềm
+ Tải xuống các tệp thông thường từ internet
+ Bất cứ điều gì bạn có thể nghĩ ra
• Tập lệnh dữ liệu người dùng EC2 chạy với người dùng gốc
**1.3 EC2 instance types:example**
Có hàng trăm loại phiên bản EC2, nhưng đây là 5 loại :

![image](https://user-images.githubusercontent.com/46096038/196630456-353fcb07-1ebd-46d8-81e1-4ec4281fffde.png)

ví dụ : t2 là loại miễn phies có thể nhận được tối đa 750h mỗi tháng
 **A1.Thực hành**
 Khởi chạy Phiên bản EC2 chạy Linux
• khởi chạy máy chủ ảo đầu tiên của mình bằng Bảng điều khiển AWS
• cách tiếp cận cấp cao đầu tiên đối với các thông số khác nhau
• Chúng tôi sẽ thấy rằng máy chủ web của chúng tôi được khởi chạy bằng dữ liệu người dùng EC2
• Chúng ta sẽ học cách bắt đầu / dừng / kết thúc phiên bản của chúng tôi
**2. EC2 Instance types  - Overview**
  Hiện tại có 7 loại phiên bản EC2 
  
  ![image](https://user-images.githubusercontent.com/46096038/196657089-67f63a46-fd27-41e8-9254-0082b6a1f741.png)

• Bạn có thể sử dụng các loại phiên bản EC2 khác nhau được tối ưu hóa cho các trường hợp sử dụng khác nhau (https://aws.amazon.com/ec2/instance-types/)
• AWS có quy ước đặt tên sau:
 ví dụ :m5.2xlarge
• m: lớp thể hiện
• 5: thế hệ (AWS cải thiện chúng theo thời gian)
• 2xlarge: kích thước trong lớp cá thể
**2.1 Các loại phiên bản EC2 - Mục đích chung(General Purpose)**
• Tuyệt vời cho nhiều khối lượng công việc như máy chủ web hoặc kho lưu trữ mã
• Cân bằng giữa:
+ Máy tính
+ Memory
+ Kết nối mạng
• Trong khóa học, chúng tôi sẽ sử dụng t2.micro là một mục đích chung EC2 instance

![image](https://user-images.githubusercontent.com/46096038/196658760-9f9a2a7d-3bba-4836-b162-29622ce7b61c.png)

**2.2 Các loại phiên bản EC2 - Tính toán tối ưu hóa(Compute Optimized)**
Tuyệt vời cho các tác vụ máy tính đòi hỏi bộ xử lý hiệu suất cao:
• Khối lượng công việc xử lý hàng loạt 
• Chuyển mã phương tiện 
• Máy chủ web hiệu suất cao
• Máy tính hiệu suất cao (HPC) 
• Lập mô hình khoa học & học máy 
• Máy chủ chơi game chuyên dụng
=> các phiên bản thực sự có kiểu đặc biệt này và hiện tại tất cả các phiên bản được tối ưu hóa cho máy tính trong EC2, đều có tên C

![image](https://user-images.githubusercontent.com/46096038/196660066-96b11716-0738-482f-a6da-72f40e945b49.png)
 **2.3 Các loại phiên bản EC2 - Bộ nhớ được tối ưu hóa(Memory Optimized)**
 Hiệu suất nhanh cho khối lượng công việc xử lý các tập dữ liệu lớn trong bộ nhớ
• Trường hợp sử dụng:
• Hiệu suất cao, cơ sở dữ liệu quan hệ / không quan hệ
• Lưu trữ bộ nhớ cache quy mô web phân tán
• Cơ sở dữ liệu trong bộ nhớ được tối ưu hóa cho BI (kinh doanh thông minh)
• Các ứng dụng thực hiện xử lý thời gian thực đối với dữ liệu lớn không có cấu trúc
 => Tên các phiên bản tối ưu hóa bộ nhớ sẽ là dòng R (Ram) hoặc X ( một bộ nhớ cao) và một bộ nhớ Z
 
 ![image](https://user-images.githubusercontent.com/46096038/196660742-844f38b1-5843-4bd5-9da2-5dbb9415fc1f.png)

**2.4 Các loại phiên bản EC2 - Tối ưu hóa bộ nhớ (Storage Optimized)**
Tuyệt vời cho các tác vụ lưu trữ nhiều yêu cầu cao, đọc và ghi tuần tự quyền truy cập vào các tập dữ liệu lớn trên bộ nhớ cục bộ
• Trường hợp sử dụng:
• Hệ thống xử lý giao dịch trực tuyến tần số cao (OLTP)
• Cơ sở dữ liệu quan hệ & NoSQL
• Bộ nhớ đệm cho cơ sở dữ liệu trong bộ nhớ (ví dụ: Redis)
• Ứng dụng kho dữ liệu
• Hệ thống tệp phân tán
=> tên của phiên bản tối ưu hóa tìm kiếm AWS sẽ bắt đầu bằng I,G hoặc H
![image](https://user-images.githubusercontent.com/46096038/196661539-13bd6bb4-337e-4ee5-90eb-8efa8fadb44f.png)
