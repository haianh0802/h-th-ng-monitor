### 1. Lịch sử về check_mk

Năm 2008 check_mk được ra mắt như là một plugins hỗ trợ và bổ sung thêm cho lõi nagios. Để có thể giúp cho giải pháp nagios hoàn thiện hơn các nhược điểm mà nagios còn mắc phải

Năm 2010 dự án OMD (Open Monitoring Distribution) được khởi động bởi Mathias Kettner. Đã kết hợp nhiều sản phẩm để có thể tạo ra sự linh hoạt trong giám sát hơn. Lúc đó có 2 phiên bản distro của OMD là OMD-LABS và CHECK_MK RAW ( OMD thường) . OMD sử dụng nhân là nagios kết hợp thêm nhiều sản phẩm mã nguồn mở để tạo ra một sản phẩm tối ưu cho nhu cầu giám sát, cảnh báo và hiển thị

Năm 2015 phiên bản đơn giản của OMD đã được ra mắt gọi là CHECK_MK vào lúc đó có 2 phiên bản của là: CHECK_MK RAW EDITION(CRE) và CHECK_MK ENTERPRISE EDITION(CEE). Hiện nay có thêm một phiên bản mới phiên bản này dựa trên phiên bản CEE được gọi là Checkmk Managed Services Edition

### 2. Phân biệt OMD-LABS và OMD(check_mk)

- OMD là một phiên bản nhỏ của OMD-LABS nó tập chung chủ yếu vào việc phát triển check_mk.

- OMD-LABS là phiên bản nâng cấp của OMD nên nó có thêm một số sản phẩm mã nguồn mở khác được tích hợp ví dụ như : Naemon; Icinga2; Grafana/Influxdb …

- Trang web mặc định của OMD-LABS là Thruk

- Từ phiên bản OMD-LABS 3.0 trở đi đã remove một số phần mềm là: Nagios3; Icinga 2, Check_mk, Nagvis

### 3. Khái niệm về CHECK_MK

Là một giải pháp giám sát dựa trên mã nguồn mở. Có lõi là nagios core.

Check_mk được tạo ra với mục đích giải bài toán hiệu năng cho nagios. Giúp cho việc mở rộng hệ thống giám sát dễ dàng hơn

![image](https://user-images.githubusercontent.com/101684058/165202653-77b3c8ef-8799-4723-b40d-2448163e00f8.png)

Với tính năng được tích hợp với nhiều sản phẩm thì check_mk được cấu hình đơn giản hơn nhiều so với lõi nagios trước kia. Check_mk bổ sung thêm một số chức năng

- Thời gian check tiêu chuẩn được giảm từ 5 phút xuống 1 phút
- Có thể cấu hình bằng giao diện WEB
- Có chức năng giám sát phân tán
- Có bảng điều khiển
- Có bảng thống kê số liệu
- Có biểu đồ hiển thị
- etc…

### 4. Các phiên bản của Check_mk
Đến thời điểm hiện tại thì nagios có 3 phiên bản chính và có sẵn

- Check_MK Raw Edition (CRE)
- Check_MK Enterprise Edition (CEE)
- Checkmk Managed Services Edition (CME)

### 5. Các khái niệm trong check_mk
##### Livestatus
- Là một phần quan trọng trong check_mk. Nó giúp cho check_mk truy xuất dữ liệu một cách nhanh chóng
- Livestatus sẽ sử dụng socket để lấy dữ liệu để trả lời truy vấn dó đó tốc độ truy vấn của nó không còn phụ thuộc vào tốc độ I/O như là lưu dữ liệu trong file
- Khi truy xuất dữ liệu bằng command line thì livestatus sẽ phân biệt chữ hoa và chữ thường
- Livestatus sẽ sử dụng socket để check dữ liệu do đó công việc được phân đều cho các CPU
##### Multisite – Giao diện web
- Multisite là một giao diện web được check_mk áp dụng để thay thế cho nagios web.
- Nó được sử dụng để xem thông tin và kiểm soát hệ thống giám sát.
- Kết hợp WATO để có thể hỗ trợ việc cấu hình bằng website
- WATO là tập hợp nhiều modules được sử dụng để cấu hình cho check_mk server
- Mỗi khi có thay đổi cần chọn cập nhật thay đổi
- Có sẵn các agent giám sát được lưu trữ và hiển thị sẵn trên web
- Nó có phiên bản tối ưu hóa cho điện thoại

![image](https://user-images.githubusercontent.com/101684058/165203160-9ae8dd15-0bc9-4ca2-adfb-2d140f54daf1.png)

##### EVENT CONSOLE
- Ngoài việc giám sát theo khoảng thời gian check bình thường còn có một loại giám sát theo sự kiện
- Event console là hệ thống tích hợp theo dõi sự kiên từ các nguồn như syslog; SNMP traps; Windows event logs …
- Những sự kiện xảy ra không được xử lý bằng lõi của check_mk mà được xử lý bằng một dịch vụ riêng biệt
##### Round Robin Database(RRD)
- Đây là dạng DB mặc định mà check_mk dùng để lưu trữ thông tin
- Thông tin của DB được lưu trữ dưới dạng bảng và cột để lưu trữ dữ liệu
- Có thể hợp nhất được dữ liệu của một khoảng thời gian lại vào làm một
- Có thể truy vấn được dữ liệu trong RRD bằng live status language
- Lưu ý ngôn ngữ truy vấn này phân biệt chữ hoa và chữ thường
- Có thể sử dụng các headers để lọc thông tin hiển thị từ các truy vấn được sử dụng
- Khi muốn truy vấn thống kê thì có các giá trị và các toán tử được định nghĩa sẵn để sử dụng
- Khi dữ liệu được lưu đầy thì nó sẽ ghi đè lên dữ liệu cũ

![image](https://user-images.githubusercontent.com/101684058/165203266-fa63462f-9a3e-4897-9084-c42b6f016d89.png)

##### Site
- Để có thể thực hiện việc giám sát thì cần tạo ra một site để có thể sử dụng
- Một server có thể tạo ra được nhiều site
- Để đăng nhập được vào site thì cần có user để đăng nhập và user được phân thành 3 loại user: Administrator; Guest; Normal monitoring
- Có 2 user mặc định có quyền Administrator là omdadmin và cmkadmin
- Site là cách gọi của sản phẩm được tạo ra từ Multisite

### 6. Cấu trúc của check_mk

![image](https://user-images.githubusercontent.com/101684058/165203352-30567db7-bbdb-4fd8-8d62-b1115f3f83a2.png)

- Các lõi sẽ gọi xuống check_mk để thực hiện chức năng kiểm tra của nó
- sau khi check thì livestatus sẽ hiển thị thông tin của mk lên website
- PNP4nagios: được sử dụng để xử lý dữ liệu để chuyển sang dạng biểu đồ
- Nagvis : được sử dụng để vẽ lại mô hình giám sát giúp người dùng có thể nhìn một cách dễ dàng hiểu hơn
- Dữ liệu sẽ được lưu vào trong RRD

### 7. Ưu điểm trong thiết kế kiến trúc của OMD.#
OMD được xây dựng từ những đóng góp của cộng đồng về những khó khăn hay khuyết điểm mà Nagios gặp phải, từ đó đưa ra quyết định cần tích hợp thêm những sản phẩm gì để cải thiện.

Việc cài đặt trở nên vô cùng đơng giản. OMD được đóng gói hoàn chỉnh trong một package, việc cài đặt và cấu hình chỉ mất khoảng 10 phút với chỉ một câu lệnh

Check_MK ra đời để giải quyết bài toán về hiệu năng mà Nagios gặp phải trong quá khứ.Cơ chế mới của Check_MK cho phép việc mở rộng hệ thống trở nên dễ dàng hơn, có thể giám sát nhiều hệ thống chỉ từ một máy chủ Nagios server.

Có 2 mô đun mà Check_MK sử dụng để cải thiện đáng kể hiệu năng là Livestatus và Livecheck.

Livestatus có những thay đổi để cải thiện hiệu năng đó là:
- Livestatus cũng sử dụng Nagios Event Broker API như NDO, nhưng nó sẽ không chủ động ghi dữ liệu ra. Thay vào đó, nó sẽ mở ra một socket để dữ liệu có thể được lấy ra theo yêu cầu.
- Livestatus tiêu tốn ít CPU.
- Livestatus không làm cho Disk I/O thay đổi khi truy vấn trạng thái dữ liệu.
- Không cần cấu hình. Không cần cơ sở dữ liệu. Không cần quản lý.
Livecheck hoạt động như thế nào để cải thiện được hiệu năng :
- Livecheck sử dụng các helper process, các core giao tiếp với helper thông qua Unix socket (điều này không xảy ra trên file system).
- Chỉ có một một helper program được fork thay vì toàn bộ Nagios Core.
- Các tiến trình fork được phân tán trên tất cả các CPU thay vì chỉ một như trước.
- Process VM size tổng chỉ khoảng 100KB.

# Cài đặt Check_mk trên Centos7
Cài đặt gói wget

`yum install wget -y `

![image](https://user-images.githubusercontent.com/101684058/165239319-61afd61e-38df-401e-bde0-64a14586fbd1.png)

Khai báo repo

`yum install epel-release -y`

![image](https://user-images.githubusercontent.com/101684058/165239635-253c4399-ab1f-427d-a391-363ddef0b143.png)

Vào Centos7 click vào https://checkmk.com/de/download?edition=cfe&version=stable&dist=redhat để tải check_mk 

Cài đặt check_mk bằng link vừa download.
`yum install check-mk-free-2.0.0p23-el7-38.x86_64.rpm`

![image](https://user-images.githubusercontent.com/101684058/165264899-e90fd09d-bea8-419e-91ec-7508ec6681c5.png)

Mở port 80 để sử dụng dịch vụ httpd

`firewall-cmd --permanent --add-port=80/tcp`

`firewall-cmd --reload`

![image](https://user-images.githubusercontent.com/101684058/165265879-f27b637a-09e3-4af7-892d-ce42b098ca56.png)

Tắt selinux
`setenforce 0`

![image](https://user-images.githubusercontent.com/101684058/165266248-c958532d-7c95-421f-a8fb-7df504b42938.png)

Tạo và khởi động site

`omd create monitoring`

`omd start monitoring`

![image](https://user-images.githubusercontent.com/101684058/165266589-20d12f22-b238-4ac0-b9f1-c20b3a0c18f0.png)

Đặt mật khẩu cho site
`su - monitoring`

`htpasswd -m ~/etc/htpasswd omdadmin`

![image](https://user-images.githubusercontent.com/101684058/165268514-fd75906c-e2e6-41d6-9554-b5caff89e857.png)


Đăng nhập vào trang web bằng tài khoản admin

`http://ip_address/monitoring/check_mk`

![image](https://user-images.githubusercontent.com/101684058/165267567-282ff290-4d36-4adc-8a54-3bb41c67f119.png)

![image](https://user-images.githubusercontent.com/101684058/165268588-45adc59e-6c2b-4f9d-9d0d-338e78068ad5.png)

## Các bước thực hiện với client centos 7

 Tìm agent phù hợp
 
 Trên các website của check_mk server khi bạn cài đặt và đăng nhập vào nó sẽ hỗ trợ và hiển thị cho bạn các agent 3 loại agent. Việc của bạn là chọn agent phù hợp với hệ điều hành của mình. Ở đây tôi cài đặt agent trên centos 7 nên tôi sẽ chọn agent có đuôi là .rpm để tiến hành cài đặt
 

![image](https://user-images.githubusercontent.com/101684058/165673109-427bcf2b-d37c-45e8-b7e0-4a260db89001.png)

 Cài đặt gói wget

`yum install wget -y `

![image](https://user-images.githubusercontent.com/101684058/165673459-0e11d959-a618-426c-b68d-59837123834d.png)

`wget http://192.168.154.135/monitoring/check_mk/agents/check-mk-agent-2.0.0p23-1.noarch.rpm`

![image](https://user-images.githubusercontent.com/101684058/165673861-91a5cd9d-30f5-4057-a8da-8bb8bbe33ad7.png)

Cấp quyền thực thi cho file vừa download về

`chmod +x check-mk-agent-2.0.0p23-1.noarch.rpm`

![image](https://user-images.githubusercontent.com/101684058/165674054-f7598b65-03fc-481e-8733-6d5f4f8652ce.png)

Cài đặt agent

`rpm -ivh check-mk-agent-2.0.0p23-1.noarch.rpm`

![image](https://user-images.githubusercontent.com/101684058/165674134-93c4318c-1d69-4652-ab24-ff41faac04e1.png)

Cài đặt xinetd

`yum install xinetd -y`

![image](https://user-images.githubusercontent.com/101684058/165674221-729b8ff7-05d8-4067-898f-c64dfafd521a.png)

Khởi động xinetd

`systemctl start xinetd`
`systemctl enable xinetd`

![image](https://user-images.githubusercontent.com/101684058/165674284-b6e687da-bf8a-48bf-9488-ec4d5ad547f9.png)

Cài đặt gói net-tools để kiểm tra dễ dàng hơn

`yum install net-tools -y`

![image](https://user-images.githubusercontent.com/101684058/165674334-cfa8d47a-e5ba-4f8f-b4fb-50fb0ff3650e.png)

 Mở port trên client để có thể giao tiếp với check_mk server

`vi /etc/xinetd.d/check_mk`

![image](https://user-images.githubusercontent.com/101684058/165675123-db20c305-a4e0-4664-88ee-53c3fe05cb9a.png)

Kiểm tra port mặc định của check_mk sử dụng để giám sát được chưa

![image](https://user-images.githubusercontent.com/101684058/165675210-0536dc40-5620-4243-bb96-0001f38939bb.png)

Mở port trên firewall

 `firewall-cmd --add-port=6556/tcp --permanent`
 `firewall-cmd --reload`

![image](https://user-images.githubusercontent.com/101684058/165675257-22b5a688-9978-4791-9658-19b23339295a.png)

Tắt selinux

`setenforce 0`

![image](https://user-images.githubusercontent.com/101684058/165675327-ff3f2d06-0568-4629-a2e6-9f8a88a44a9b.png)

## Một số thao tác cơ bản
#### Đổi mật khẩu
Chọn User ->  Change Password
![image](https://user-images.githubusercontent.com/101684058/165701245-eac384ef-1793-4c6b-bf9b-1bbb16e38280.png)

Điền mật khẩu cũ và mật khẩu mới vào rồi chọn Save

![image](https://user-images.githubusercontent.com/101684058/165701647-4601bb91-2393-454a-858a-f26122c22cd2.png)

#### Thêm máy chủ vào hệ thống giám sát

![image](https://user-images.githubusercontent.com/101684058/165703217-b8133bba-163b-47ee-9a8d-40bb66d1c552.png)

![image](https://user-images.githubusercontent.com/101684058/165703293-4c5ffe6a-5300-4b5e-98f1-e54569baa73f.png)

Điền hostname và ip address và chọn save

![image](https://user-images.githubusercontent.com/101684058/165703474-da8a2da1-f943-4abb-b8fe-e8a78dbafbcf.png)
 
 Bạn có thể click vào "+" để dám sát dịch vụ hoặc vào "x" để không dám sát dịch vụ. Có thể click fix all để chọn giám sát tất cả
 
![image](https://user-images.githubusercontent.com/101684058/165706450-2bb784cc-1cd3-40be-a0ed-ef6e7774f671.png)

Có những thay đổi không đc áp dụng tự động click vào đây để kích hoạt

![image](https://user-images.githubusercontent.com/101684058/165707701-b2a40221-e8c0-4be0-b3a2-b647178bf7af.png)

Bây giờ các thay đổi đã được kích hoatl

![image](https://user-images.githubusercontent.com/101684058/165707951-115ea8c7-4717-42b6-a034-59d7d27e2080.png)

Tổng quan về tất cả các dịch vụ 
![image](https://user-images.githubusercontent.com/101684058/165708882-c9411414-d9ea-4f57-8644-732ec74812ca.png)


