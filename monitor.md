# Monitoring System là gì?
Monitoring là một hệ thống dùng để thu thập thông tin về phần cứng và phần mềm của một hệ thống IT. Hệ thống monitoring có thể thu thập từ trạng thái của của server (CPU, memory, network, …) cho đến những thông tin chi tiết về cách server xử lý request đến từ người dùng (số lượng requests/s, thời gian server xử lý requests, …).

Một hệ thống monitoring sẽ giúp chúng ta có một cái nhìn dễ dàng về chất lượng và những vấn đề xảy ra với sản phẩm. Nó sẽ tự động cảnh báo cho chúng ta ngay khi phát hiện ra điều bất thường. Bây giờ, thay vì được người dùng thông báo rằng server gặp trục trặc, chúng ta sẽ sớm phát hiện và giải quyết trước khi người dùng nhận ra. Hơn nữa, đối với các hệ thống đủ lớn và phức tạp, hệ thống monitoring còn giúp chúng ta biết được những thành phần nào hay gặp sự cố để có thể tập trung cải thiện chất lượng.

Người dùng luôn là mục tiêu cuối cùng của sản phẩm. Hiểu được những gì thực sự quan trọng đối với người dùng và xây dựng được các công thức tính toán các yếu tố này giúp chúng ta tập trung vào những thứ cần thiết và có được một cái nhìn chính xác về sự hiệu quả của sản phẩm. Từ đó, chúng ta có thể xây dựng một hệ thống monitoring hiệu quả để đảm bảo mục tiêu cụ thể mà chúng ta đề ra.

# Monitoring System ở Got It

### Elastic Stack

Elastic stack là một tập hợp các công nghệ dùng để thu thập, biến đổi, lưu trữ và phân tích dữ liệu với thành phần chính là Elasticsearch.

![image](https://user-images.githubusercontent.com/101684058/165198523-50fd37ea-15d1-4f8f-815c-5d42da749257.png)

Về khía cạnh monitoring, beats sẽ được sử dụng để thu thập thông tin của server. Hệ thống monitoring của Got It sử dụng:

- Metricbeat: Thu thập metrics về server (CPU, memory, …)
- Filebeat: Thu thập logs của các services.
- Heartbeat: Ping để kiểm tra xem các services có còn hoạt động không.
Logstash được sử dụng để biến đổi dữ liệu theo cách mà chúng ta mong muốn. Sau đó, tất cả dữ liệu sẽ được lưu trong Elasticsearch và được hiển thị qua dashboard trong Kibana.

### Monitoring System của Got It hoạt động thế nào?

![image](https://user-images.githubusercontent.com/101684058/165198614-b2c24c42-7b38-473c-9f9e-3645cb0548d5.png)

Metricbeat, Heartbeat và Filebeat sẽ thu thập các thông tin về hệ thống và gửi trực tiếp về Elasticsearch. Ở đây, chúng ta không dùng Logstash để biến đổi dữ liệu mà thay vào đó Ingest Node của Elasticsearch sẽ được sử dụng để giảm bớt đi một layer trong hệ thống, khiến hệ thống đơn giản hơn. Dữ liệu thu thập được từ hệ thống monitoring thường khá thường xuyên và lớn nên các kỹ sư ở Got It luôn phải có phương án kỹ lưỡng về thời gian lưu trữ chúng trên Elasticsearch cũng như backup thường xuyên để tránh mất dữ liệu.

### Kết luận

Đối với các công ty lớn, hệ thống monitoring là công cụ không thể thiếu để đảm bảo chất lượng của sản phẩm cũng như trải nghiệm của người dùng. Bài viết này miêu tả một trong những hệ thống monitoring mà các kỹ sư tại Got It tự tìm hiểu, xây dựng và sử dụng thành công. Lưu ý rằng, ngoài hệ thống trên, các sản phẩm của Got It còn được giám sát cẩn thận bởi các monitoring system khác (mà không được nhắc đến trong bài viết này) vì có rất nhiều khía cạnh khác nhau của các hệ thống IT mà chúng ta cần bảo vệ.
