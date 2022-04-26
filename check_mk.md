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


![image](https://user-images.githubusercontent.com/101684058/165210567-1bd77d73-0cd8-40cd-a022-f0b2bbea05d4.png)


![image](https://user-images.githubusercontent.com/101684058/165264899-e90fd09d-bea8-419e-91ec-7508ec6681c5.png)

![image](https://user-images.githubusercontent.com/101684058/165265879-f27b637a-09e3-4af7-892d-ce42b098ca56.png)

![image](https://user-images.githubusercontent.com/101684058/165266248-c958532d-7c95-421f-a8fb-7df504b42938.png)

![image](https://user-images.githubusercontent.com/101684058/165266589-20d12f22-b238-4ac0-b9f1-c20b3a0c18f0.png)

![image](https://user-images.githubusercontent.com/101684058/165268514-fd75906c-e2e6-41d6-9554-b5caff89e857.png)

![image](https://user-images.githubusercontent.com/101684058/165267567-282ff290-4d36-4adc-8a54-3bb41c67f119.png)

![image](https://user-images.githubusercontent.com/101684058/165268588-45adc59e-6c2b-4f9d-9d0d-338e78068ad5.png)



