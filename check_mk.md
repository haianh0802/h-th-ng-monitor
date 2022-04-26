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
Là một phần quan trọng trong check_mk. Nó giúp cho check_mk truy xuất dữ liệu một cách nhanh chóng
Livestatus sẽ sử dụng socket để lấy dữ liệu để trả lời truy vấn dó đó tốc độ truy vấn của nó không còn phụ thuộc vào tốc độ I/O như là lưu dữ liệu trong file
Khi truy xuất dữ liệu bằng command line thì livestatus sẽ phân biệt chữ hoa và chữ thường
Livestatus sẽ sử dụng socket để check dữ liệu do đó công việc được phân đều cho các CPU
##### Multisite – Giao diện web
Multisite là một giao diện web được check_mk áp dụng để thay thế cho nagios web.
Nó được sử dụng để xem thông tin và kiểm soát hệ thống giám sát.
Kết hợp WATO để có thể hỗ trợ việc cấu hình bằng website
WATO là tập hợp nhiều modules được sử dụng để cấu hình cho check_mk server
Mỗi khi có thay đổi cần chọn cập nhật thay đổi
Có sẵn các agent giám sát được lưu trữ và hiển thị sẵn trên web
Nó có phiên bản tối ưu hóa cho điện thoại
