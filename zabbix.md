## 1. Tổng quan vể Zabbix.
Zabbix là gì? Zabbix là một công cụ mã nguồn mở nổi tiếng giải quyết cho ta các vấn đề về giám sát – là phần mềm sử dụng các tham số của một mạng, tình trạng và tính toàn vẹn của Server cũng như các thiết bị mạng.

Zabbix sử dụng một cơ chế thống báo linh hoạt và khả năng tuỳ biến cao cho phép người dùng cấu hình email hoặc sms để cảnh báo dựa trên sự kiện được ta thiết lập sẵn. Ngoài ra Zabbix cung cấp báo cáo và dữ liệu chính xác dựa trên cơ sở dữ liệu. Điều này khiến cho Zabbix trở nên lý tưởng hơn, thích hợp phục vụ cho hệ thống mạng tầm trung và lớn của các doanh nghiệp hiện tại với mức chi phí đầu tư vừa phải.

Zabbix được sáng lập bởi Alexei Vladishev và hiện tại được phát triển cũng như hỗ trợ bởi tổ chức Zabbix SIA. Zabbix được viết và phát hành dưới bản quyền General Public License GPL phiên bản 2

Tất cả báo cáo, thống kê cũng như cấu hình thông số của Zabbix có thể dễ dàng truy cập qua giao diện web tinh tế đẹp mắt. Giúp chúng ta theo dõi được tình trạng hệ thống thiết bị server, dịch vụ,..

## 2. Ưu/nhược điểm của Zabbix là gì. 
#### 2.1 Ưu điểm.
Ưu điểm của Zabbix là gì mà được đánh giá là mã nguồn mở được đánh giá cao? Bởi vì có các ưu điểm sau mà bạn không nên bỏ qua:

- Giám sát, tự động tìm phát hiện server và hệ thống mạng.
- Hỗ trợ server cài đặt trên dòng hệ điều hành Unix/Linux.
- Hỗ trợ máy trạm client nhiều hệ điều hành.
- Giao diện web cực kì tinh tế và đẹp mắt.
- Thông báo sự cố qua email, OTP App và SMS.
- Mã nguồn mở, chi phí đầu tư thấp.
- Biểu đổ theo dõi và báo cáo qua giao diện.
- Kiểm soát theo dõi việc đăng nhập.
- Linh hoạt trongphân quyền người dùng.
- Nhiều Plugin hỗ trợ.

#### 2.2 Nhược điểm.
- Không có giao diện web mobile hỗ trợ.
- Không phù hợp với hệ thống mạng lớn, nhiều thiết bị client cần giám sát. Lúc này phát sinh vấn đề hiệu suất về PHP và Database, v..v..
- Thiết kế template/alerting rule đôi khi khá phức tạp.

## 3. Các công việc mà Zabbix thực hiện 
#### Thực hiện chức năng giám sát toàn diện 
- Giám sát phần cứng: Zabbix thực hiện giám sát các vấn đề như nhiệt độ máy chủ, công tắc bộ định tuyến, ... thông qua SNMP.

Dành cho các bạn chưa rõ, SNMP (Simple Network Management Protocol) là tập hợp các giao thức có chức năng kiểm tra hoạt động và hỗ trợ vận hành từ xa cho các thiết bị mạng như router, switch hay server.

Tuy nhiên, bạn không cần thiết phải giám sát phần cứng thường xuyên. Vì nó không ảnh hưởng đến việc quản lý của doanh nghiệp

- Giám sát hệ thống: Là việc theo dõi các số liệu về dung lượng, tốc độ của hạ tầng như CPU, Ram, ổ cứng,... nhằm đảm bảo tài nguyên của bạn luôn đủ để sử dụng. Tránh trường hợp gây mất ổn định, hoặc khởi động lại hệ thống. Như hosting chạy trên hệ điều hành windows chỉ nên sử dụng đến giới hạn tài nguyên 80% để đảm bảo mọi hoạt động diễn ra bình thường

- Giám sát mạng: thường sử dụng với các công ty sử dụng giải pháp mạng điện toán đám mây. 

- Giám sát bảo mật: Bao gồm tường lửa, phần mềm chống DDOS, mật khẩu, sao lưu, phục hồi và các hệ thống bảo mật được các nhà cung cấp cài đặt sẵn trên các giải pháp mạng. Báo cáo quá trình hoạt động của các công cụ này, sự ghé thăm của mã độc, những đường link chứa nhiều mã độc truy cập vào trang,... 

- Giám sát web: chức năng này có thể được phát triển cao hơn với nhu cầu kiểm soát của người dùng. Nó đưa ra các số liệu về thời gian tải trang, tốc độ load, thời gian phản hồi,... 

- Theo dõi nhật ký: là quá trình thu thập, lưu trữ, truy vấn dữ liệu. Bạn có thể theo dõi Nginx thông qua nhật ký 500x, lỗi PHP,... Ngoài ra, bạn có thể phát triển chức năng này bằng cách sử dụng mã nguồn mở ELKstack để đạt được .logstash, ,elasticsearch (lưu trữ + tìm kiếm), kibana (hiển thị) 

#### Phân tích lưu lượng 
Là công việc đếm ip, pv và uv. Bạn có thể sử dụng các công cụ như awk sed xxx, các công cụ của Google để phát triển mã nhúng, hoặc piwwiki để phân tích lưu lượng truy cập liên quan. 

Công việc này giúp người sử dụng theo dõi được hoạt động của trang web, số lượng traffic, chất lượng của những lượt ghé thăm, qua đó đánh giá được hiệu quả của chiến lược marketing và những vấn đề cần thay đổi. 

## 4. Các thành phần của hệ thống giám sát dịch vụ Zabbix.
- Zabbix Server: Đây là ứng dụng chương trình dịch vụ chính của dịch vụ Zabbix. Zabbix Server sẽ chịu trách nhiệm cho các hoạt động kiểm tra dịch vụ mạng từ xa, thu thập thông tin, lưu trữ, hiển thị, cảnh báo,… từ đó các quản trị viên có thể thao tác giám sát hệ thống tốt nhất.
- Zabbix Proxy: là một máy chủ được dùng cho việc quản lý nhiều nhánh hệ thống ở xa, hoặc ở các lớp mạng khác nhau. Từ Zabbix Proxy sẽ thu thập các thông tin thiết bị mạng rồi chuyển tiếp về cho máy chủ dịch vụ chính Zabbix Server.
- Zabbix Agent: để giám sát chủ động các thiết bị cục bộ và các ứng dụng (ổ cứng, bộ nhớ, …) trên hệ thống mạng. Zabbix Agent sẽ được cài lên trên Server và từ đó Agent sẽ thu thập thông tin hoạt động từ Server mà nó đang chạy và báo cáo dữ liệu này đến Zabbix Server để xử lý.
- Giao diện web: cung cấp giao diện web trên nền tảng mã nguồn PHP cùng phong cách metro tinh tế. Hiện tại có thể xem Zabbix là một trong những ứng dụng có giao diện đẹp nhất, thiết kế vị trí tính năng bắt mắt và hợp lý.

## 5.Các chức năng mà Zabbix cung cấp đến người dùng
#### Problem Detection 
Phát hiện vấn đề trên các chỉ số, với các ưu điểm như: 

- Xác định lỗi nhanh và linh hoạt 

- chia danh mục các vấn đề đã và chưa giải quyết

- Tìm kiếm nguyên nhân 

- Dự đoán xu hướng 

#### Notification and Remediation
Chức năng thông báo, khởi động khi phát hiện vấn đề và gửi thông báo đến các thiết bị đã được cài đặt từ trước. Người sử dụng có thể cài đặt mức độ thông báo, thời gian lặp lại

#### Security and Authentication
Bảo vệ dữ liệu của bạn ở nhiều cấp độ, đảm bảo an ninh dữ liệu tối đa, bao gồm: 

- Mã hóa mạnh mẽ tất cả các thông tin có trên  Zabbix

- Sử dụng các phương pháp xác thực người dùng : Mở LDAP, Active Director

- Mã Zabbix được mở để kiểm tra bảo mật
#### Metric Collection 
Đây là chức năng thu thập dữ liệu từ các hệ thống, máy chủ; tính toán và tổng hợp các thông số; giám sát website người dùng cuối, trên các phương pháp:  Multi-platform Zabbix Agent; SNMP và IPMI Agent

#### Effortless Deployment 
Cung cấp các mẫu out of the box, cho phép bạn tạo mẫu, sử dụng hàng trăm mẫu templates được phát triển bằng cộng đồng mở, giám sát hàng nghìn thiết bị bằng cách sử dụng các mẫu cấu hình tương tự; tiết kiệm thờigian thiết lập cho người dùng một cách linh động, hiệu quả. 

#### Auto - Discovery
Được biết đến là một chức năng tự động thêm các thao tác cơ bản như thay đổi / thêm/ xóa. Với các chức năng phân cấp:

- Network discovery: quét các thông số trên internet như trạng thái IP, thời gian hoạt động hoặc không hoạt động,... một cách định kỳ theo lập trình của người sử dụng.

- Low-level discovery: tự động tạo mục, trường và biểu đồ cho các phần khác nhau trên hệ thống. 

- Auto-registration of the active agents: thực hiện chức năng ghi nhận và theo dõi các agent đang hoạt động trên phương thức tự động. 
