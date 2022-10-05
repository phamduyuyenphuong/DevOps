1.What's AWS
+ Cloud Provider
+ Cung cấp các máy chủ và dịch vụ mà bạn có thể sử dụng nhu cầu và quy mô dễ dàng
+ AWS đã cách mạng hóa CNTT theo thời gian
+ AWS cung cấp sức mạnh cho một số trang web lớn nhất trên thế giới
  • Amazon.com 
  • Netflix
 2. AWS Cloud Use Cases
 + Xây dựng các ứng dụng phức tạp và có khả năng mở rộng và có thể áp dụng cho nhiều nhóm ngành
 + Các trường hợp sử dụng bao gồm
  • Enterprise IT, Backup & Storage, Big Data analytics 
  • Website hosting, Mobile & Social Apps 
  • Gaming
  3.AWS Regions
  + all the world
  + names can be us-east-I, eu-west-3...
  + là cụm trung tâm dữ liệu => nhiều cụm 
  how choose an AWS Region ?
  • Tuân thủ các yêu cầu pháp lý và quản trị dữ liệu: dữ liệu không bao giờ rời khỏi khu vực mà không có sự cho phép rõ ràng của bạn
  • Gần khách hàng: giảm độ trễ
  • Các dịch vụ khả dụng trong một Khu vực: các dịch vụ mới và các tính năng mới không có sẵn ở mọi Khu vực
  • Giá cả: giá cả khác nhau giữa các khu vực và minh bạch trong trang giá dịch vụ
  AWS Availability Zones
  + Mỗi khu vực có nhiều vùng khả dụng (min = 2, max = 6, thường = 3)
  + Mỗi vùng khả dụng (AZ) là một hoặc nhiều trung tâm dữ liệu rời rạc có nguồn, mạng và kết nối dự phòng
  + Chúng tách biệt với nhau, để chúng bị cô lập khỏi thảm họa
  + Chúng được kết nối với băng thông cao, mạng có độ trễ cực thấp
  
AWS có các dịch vụ Toàn cầu:
• Identity and Access Management (IAM)
• Route 53 (DNS service)
• CloudFront (Content Delivery Network)
• WAF (Web Application Firewall)
Hầu hết các dịch vụ AWS cũng sẽ nằm trong phạm vi khu vực
chẳng hạn như Amazon EC2, Elastic Beanstalk, Lambda và Rekognition .


 3.IAM: users & groups (danh tính và quản lý truy cập)
  IAM = Identity and Access Management, Global service
  Đây là một dịch vụ toàn cầu bởi vì trong IAM, chúng tôi sẽ tạo ra người dùng và chỉ định họ vào nhóm.
  Tạo 1 tài khoản gốc (default) => người dùng gốc của các tài khoản
  Tạo người dùng trong IAM, 1 người dùng đại diện cho một người trong tổ chức và những người dùng có thể được nhóm lại cùng nhau nếu nó có ý nghĩa (một người có thể thuộc nhiều nhóm)
  Vì sao tạo users và group? Cho phép họ sử dụng tài khoản AWS
  Permissions :
  user hoặc group có thể được chỉ định cái được gọi là tài liệu JSON nó 
![image](https://user-images.githubusercontent.com/46096038/194003009-b2d27d5a-7ab0-4547-94df-58fb60d45b45.png)
Chúng tôi đang cho phép người dùng của mình để sử dụng một số dịch vụ trong AWS.

Vì vậy, các chính sách này sẽ giúp chúng tôi xác định quyền của người dùng của chúng tôi.
trong AWS, bạn áp dụng một nguyên tắc được gọi là nguyên tắc đặc quyền ít nhất.
 - IAM không yêu cầu lựa chọn khu vực

Root account 
![image](https://user-images.githubusercontent.com/46096038/194008286-84eca978-95b7-4cb0-9de4-acb64c72aec5.png)
IAM account
![image](https://user-images.githubusercontent.com/46096038/194008704-87a14a05-d3f1-4d55-80ab-4a1d8994e12d.png)

3.1 **Chính sách của IAM**:
![image](https://user-images.githubusercontent.com/46096038/194010397-86814559-35d5-4bd0-87e5-6e845e6c3be3.png)

 có 1 group và đính kèm chính sách ở cấp độ group => chính sách sẽ được áp dụng cho mọi thành viên của nhóm (có quyền truy cập và kế thừa chính sách này)
 => chính sách nội tuyến có chính sách chỉ được gắn với người dùng.
Vì vậy, người dùng đó có thể hoặc không thể thuộc một nhóm mà bạn có thể có các chính sách nội tuyến cho bất kỳ người dùng nào bạn muốn.

**3.2 IAM Policies Structure (cấu trúc chính sách):**

![image](https://user-images.githubusercontent.com/46096038/194011171-01c5c60e-9590-4a40-b37f-22a08a545fce.png)

- Version : thường là 2012-10-17 (phiên bản ngôn ngữ chính sách)
- ID : Cách xác định chính sách đó ( tùy chọn)
- Một hoặc nhiều Statement
 + Sid : một ID câu lệnh, là một định danh cho câu lệnh(tùy chọn)
 + Effect : cho phép hay từ chối quyền (Allow/ Deny)
 + Principal : account/user/role nào mà chính sách này sẽ áp dụng
 + Action : danh sách các lệnh gọi, API sẽ bị từ chối hoặc được phép dựa trên hiệu ứng
 + Resource: danh sách các tài nguyên mà các action sẽ được áp dụng.
 + Condition: điều kiện khi nào policy được áp dụng hay không (tùy chọn)
 IAM Policies
 Người dùng không thuộc group quản trị viên, có thể đính kèm quyền trực tiếp cho người dùng từ acc root 
 Có 2 cách :
 
 ![image](https://user-images.githubusercontent.com/46096038/194020681-befa66c1-1b34-403d-996b-b490a1deb239.png)

 + Thêm quyền và sử dụng chính sách đã tồn tại.
 
  ![image](https://user-images.githubusercontent.com/46096038/194021056-e9774c99-65a0-4e3c-af2e-334a86a1cae3.png)

 + Tạo hoặc thêm chính sách nội tuyến để chỉ thêm chính sách trực tiếp cho người dùng. ( Tạo nhóm mới -> thêm người dùng(có quyền admin -> đính kèm chính sách bất kỳ)
 
 ![image](https://user-images.githubusercontent.com/46096038/194022027-060b85e8-4100-4798-83e3-61629d361183.png)

 ![image](https://user-images.githubusercontent.com/46096038/194019040-0666a5eb-465b-4aa5-9f73-6ee06078ef6c.png)
 
 Có thể tự tạo policy cho riêng mình
 
 3.3 **IAM-Password Policy** (Chính sách mật khẩu)
 Chính sách bảo vệ những người dùng và nhóm khỏi bị xâm hại
 3.3.1 strong passwords = bảo mật acc càng cao
=> có thể thiết lập chính sách mật khẩu với các tùy chọn khác nhau:
 - đặt độ dài mật khẩu tối thiểu 
 - yêu cầu các loại ký tự :
  + ký tự viết hoa
  + ký tự viết thường
  + ký tự không phải chữ và số, ví dụ như dấu chấm hỏi, v.v. .
 - Cho phép hoặc không, người dùng IAM thay đổi mật khẩu của chính họ 
 - Có thể yêu cầu người dùng thay đổi pass của họ ( sau 1 tgian => pass hết hạn chảng hạn 90 ngày người dùng phải thay đổi mật khẩu của họ )
 - người dùng khi họ thay đổi mật khẩu, không thay đổi nó thành mật khẩu họ đã có hoặc thay đổi nó thành mật khẩu họ đã có trước đó 
 3.3.2 Multi Factor Authentication - MFA (Xác thực đa yếu tố - MFA)
Người dùng có quyền truy cập vào tài khoản của bạn và họ có thể làm nhiều việc, đặc biệt nếu họ là quản trị viên, họ có thể thay đổi cấu hình, xóa tài nguyên và những thứ khác
=> bảo vệ acc root
Thiết bị MFA : đang sử dụng sự kết hợp giữa **mật khẩu mà bạn biết** và **thiết bị bảo mật mà bạn sở hửu**. Và 2 thứ này kết hợp với nhau độ bảo mật sẽ cao hơn.
Lợi ích: Nếu bị mất pass do bị đánh cắp hoặc tấn công  tài khoản sẽ không bị xâm phạm vì tin tặc, cũng sẽ cần nắm giữ thiết bị vật lý có thể là điện thoại. 
ví dụ để thực hiện một đăng nhập. Rõ ràng, điều đó ít xảy ra hơn nhiều.
-- Tùy chọn thiết bị MFA trong AWS là gì:
 - Virtual MFA device 
  ![image](https://user-images.githubusercontent.com/46096038/194027419-fcf1e470-c41d-41d7-b1f9-df2bbc84a121.png)
 Google Authenticator : chỉ hoạt động trên 1 điện thoại tại một thời điểm
 Authy : đa thiết bị, hỗ trợ cho nhiều mã thông báo trên một thiết bị
 - có một thứ khác được gọi là Yếu tố thứ 2 chung hoặc Khóa bảo mật U2F (Universal 2nd Factor or U2F Security Key) và đó là một thiết bị vật lý
ví dụ: YubiKey của Yubico và Yubico là bên thứ 3 của AWS, đây là một AWS
YubiKey này hỗ trợ nhiều người dùng root và IAM bằng cách sử dụng một bảo mật duy nhất, do đó bạn không cần nhiều khóa như người dùng nếu không đó sẽ là một cơn ác mộng

![image](https://user-images.githubusercontent.com/46096038/194029560-a4c76f60-cee4-4dfa-a87b-7aaa4d46b2b9.png)

4. Truy cập AWS :
- AWS Management Console (tên người dùng, pass có thể xác nhận đa yếu tố)
- AWS Command Line Interface (CLI) ( được bảo vệ bởi các khóa truy cập)
- AWS Software developer kit(SDK) : được sử dụng bất cứ khi nào bạn muốn gọi các API từ AWS từ ứng dụng của mình (khóa truy cập)
CLI : 
+ Công cụ cho phép tương tác với các dịch vụ AWS bằng cách sử dụng các lệnh từ trình bao dòng lệnh,
+ Có quyền truy cập trực tiếp vào các API công khai của các dịch vụ AWS
+ Phát triển các tập lệnh để quản lý tài nguyên và tự động hóa một số tác vụ của mình
+ Mã nguồn mở

![image](https://user-images.githubusercontent.com/46096038/194033101-def45c4b-70f6-4064-8af5-ded3f8cf3303.png)


