### 1. Cài đặt Zabbix Server trên CentOS 7

Cài đặt Zabbix repository

`rpm -Uvh https://repo.zabbix.com/zabbix/5.0/rhel/7/x86_64/zabbix-release-5.0-1.el7.noarch.rpm`

`yum clean all`

![image](https://user-images.githubusercontent.com/101684058/165711458-313b86eb-f547-4c66-816d-37a00e7ee19d.png)

Cài đặt Zabbix Server và Zabbix Agent

`yum install zabbix-server-mysql zabbix-agent`

Cài đặt Zabbix frontend

`yum install -y centos-release-scl`

Chỉnh sửa tập tin zabbix.repo để bật cho phép cài zabbix-frontend từ repository.

`nano /etc/yum.repos.d/zabbix.repo`

Đặt giá trị enable=1 vào [zabbix-frontend]

![image](https://user-images.githubusercontent.com/101684058/165712301-0d7a063e-6776-4dbc-aeba-451f3c707b96.png)

Sau đó tiến hành cài đặt Zabbix frontend từ repository.

`yum install zabbix-web-mysql-scl zabbix-apache-conf-scl`

### 2. Cài đặt MariaDB
Thêm repository cài đặt MariaDB
Để thêm repository để cài đặt MariaDB ta tiến hành tạo file mariadb.repo như sau:

`nano /etc/yum.repos.d/mariadb.repo`

![image](https://user-images.githubusercontent.com/101684058/165713342-ba46c733-dc47-4468-a014-6a97de3a573e.png)

Cài đặt MariaDB
Sau khi tạo file repo các bạn tiến hành cài đặt MariaDB bằng lệnh sau

`yum install MariaDB-server MariaDB-client -y`

Đặt mật khẩu root

Khi quá trình cài đặt hoàn tất các bạn tiến hành đặt mật khẩu root bằng cách chạy các lệnh sau

`systemctl enable mariadb`

`systemctl start mariadb`

`mysql_secure_installation`

Tạo database cho Zabbix

Login vào MySQL bằng tài khoản root (được thiết lập khi cài đặt MariaDB, bạn có thể xem lại trong phần hướng dẩn cài đặt) với câu lệnh:

`mysql -u root -p`

Tạo User và Database cho Zabbix

![image](https://user-images.githubusercontent.com/101684058/165720460-d0d03067-0b89-4d7f-b5e7-81657065291d.png)

Import database Zabbix

Khi chạy lệnh import data và schema bạn sẽ được hỏi password, hãy nhập password bạn đã tạo ở bước trên.

`zcat /usr/share/doc/zabbix-server-mysql*/create.sql.gz | mysql -uzabbix -p zabbix`


Cấu hình Zabbix trên CentOS 7
Chỉnh sửa file zabbix_server.conf, thay đổi các thông số cho phù hợp với bạn.

nano /etc/zabbix/zabbix_server.conf

![image](https://user-images.githubusercontent.com/101684058/165721876-2faf8f3a-03c1-45a4-894c-4fd714d014ad.png)

Cấu hình PHP

Mở tập tin zabbix.conf uncomment ; php_value[date.timezone] = Europe/Riga và sửa thành Asia/Ho_Chi_Minh

`nano /etc/opt/rh/rh-php72/php-fpm.d/zabbix.conf`

![image](https://user-images.githubusercontent.com/101684058/165876737-15e2548e-50cb-4de5-9c9e-02b6450879c6.png)

Khởi động Zabbix server và agent
`systemctl restart zabbix-server zabbix-agent httpd rh-php72-php-fpm`
`systemctl enable zabbix-server zabbix-agent httpd rh-php72-php-fpm`

Thiết lập tường lửa
`firewall-cmd --add-service={http,https} --permanent`
`firewall-cmd --add-port={10051/tcp,10050/tcp} --permanent`
`firewall-cmd --reload`

![image](https://user-images.githubusercontent.com/101684058/165722728-44f0c7e7-b0c5-40b5-9327-579594394950.png)

Thiết lập Zabbix Dashboard
Sau khi hoàn tất các bước trên, bạn tiến hành mở trình duyệt và nhập địa chỉ http://ip_server_cua_ban/zabbix.

![image](https://user-images.githubusercontent.com/101684058/165723016-1944dfbc-0d23-47b9-8d2b-8f0a31107fb5.png)

![image](https://user-images.githubusercontent.com/101684058/165876944-f5487812-b09f-4a8a-b6fe-fae69775d9da.png)

Nhập thông tin database -> Next step

![image](https://user-images.githubusercontent.com/101684058/165877104-447d6162-6437-4eb5-a1c4-82fac05b2828.png)

Đặt tên Zabbiz Server -> Next step

![image](https://user-images.githubusercontent.com/101684058/165881029-15a1acfb-8765-4cbf-98ac-3573fdf6c5fe.png)

Next step

![image](https://user-images.githubusercontent.com/101684058/165881106-205a6de3-ffb0-409b-8f35-8ce25fd07e93.png)

![image](https://user-images.githubusercontent.com/101684058/165881161-05e5180b-9598-498d-9a48-ed55bdfad533.png)

Sau khi thiết lập xong, bạn đăng nhập vào Zabbix Dashboard bằng tài khoản mặc định Admin / zabbix

![image](https://user-images.githubusercontent.com/101684058/165881219-fbf60c26-8f96-40e6-ad80-e9a1c444a785.png)

Giao diện Zabbix

![image](https://user-images.githubusercontent.com/101684058/165882558-989fc19a-32d4-4ee2-a873-adf60daefcdb.png)


