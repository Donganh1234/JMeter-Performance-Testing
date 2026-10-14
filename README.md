# Kiểm thử hiệu năng website bằng Apache JMeter

## 1. Giới thiệu

Apache JMeter là công cụ mã nguồn mở được sử dụng để kiểm thử hiệu năng của website và các ứng dụng. Công cụ cho phép mô phỏng nhiều người dùng gửi yêu cầu đến hệ thống, từ đó thu thập và phân tích các chỉ số như thời gian phản hồi, số lượng yêu cầu và tỷ lệ lỗi.

### Mục tiêu thực hiện:

Làm quen với giao diện và các thành phần cơ bản của Apache JMeter.

Xây dựng kịch bản kiểm thử HTTP Request.

Thực hiện kiểm thử và thu thập kết quả.

Phân tích các chỉ số hiệu năng thông qua Aggregate Report.

### Công cụ sử dụng: Apache JMeter 5.6.3.

## 2. Kịch bản kiểm tra

### 2.1. Thread Group

Số lượng người dùng ảo (Number of Threads): 5.

Thời gian chạy (Duration): 30 giây.

Ramp-up period: 5 giây.

Loop Count: Infinite.



### 2.2. HTTP Request

Protocol: HTTPS.

Website kiểm thử: https://example.com/

Method: GET.

Path: /.

Content encoding: UTF-8.



### 2.3. Listeners

Sử dụng hai Listener để quan sát và tổng hợp kết quả:

View Results Tree: Hiển thị kết quả của từng yêu cầu, mã phản hồi và thời gian xử lý.

Aggregate Report: Tổng hợp số lượng yêu cầu, thời gian phản hồi trung bình, các phân vị thời gian phản hồi và tỷ lệ lỗi.



## 3. Kết quả kiểm tra

### 3.1. Kết quả View Results Tree

Trong quá trình kiểm thử, một yêu cầu được chọn ghi nhận các thông số:

Response code: 200.

Response message: OK.

Load time: 67 ms.

Latency: 67 ms.

Error Count: 0.

Kết quả cho thấy yêu cầu được chọn đã nhận phản hồi HTTP 200 và không ghi nhận lỗi.

<img width="1442" height="823" alt="image" src="https://github.com/user-attachments/assets/dd4b2ca2-d343-4c2d-8c6a-b128f9dc59d8" />



### 3.2. Kết quả Aggregate Report

Kết quả tổng hợp từ lần chạy kiểm thử:

Total requests: 2.217

Average response time: 62 ms

Median response time: 59 ms

90th percentile response time: 68 ms

95th percentile response time: 74 ms

99th percentile response time: 91 ms

Minimum response time: 51 ms

Maximum response time: 1.180 ms

Error rate: 0,00%

<img width="1484" height="824" alt="image" src="https://github.com/user-attachments/assets/05f01136-a573-468e-b2f4-85e2946fce4a" />




## 4. Phân tích kết quả kiểm tra

### 4.1. Số lượng yêu cầu

JMeter ghi nhận tổng cộng 2.217 yêu cầu trong lần kiểm thử. Đây là số lượng yêu cầu thực tế được ghi nhận trong khoảng thời gian chạy 30 giây với 5 người dùng ảo.

### 4.2. Tỷ lệ lỗi

Tỷ lệ lỗi ghi nhận là 0,00%, cho thấy không có yêu cầu nào bị đánh dấu lỗi trong báo cáo tổng hợp của lần kiểm thử này.

### 4.3. Thời gian phản hồi

Thời gian phản hồi trung bình là 62 ms và thời gian phản hồi trung vị là 59 ms. Hai chỉ số cho thấy phần lớn yêu cầu được xử lý trong khoảng thời gian tương đối ngắn ở điều kiện thử nghiệm này.

### 4.4. Phân tích các phân vị

P90 = 68 ms: 90% yêu cầu có thời gian phản hồi không vượt quá 68 ms.

P95 = 74 ms: 95% yêu cầu có thời gian phản hồi không vượt quá 74 ms.

P99 = 91 ms: 99% yêu cầu có thời gian phản hồi không vượt quá 91 ms.

Các phân vị cho thấy phần lớn yêu cầu có thời gian phản hồi thấp. Tuy nhiên, thời gian phản hồi lớn nhất đạt 1.180 ms, cho thấy vẫn có một số yêu cầu chậm hơn đáng kể so với mức trung bình.



## 5. Kết luận

Qua bài thực hành, em đã biết cách xây dựng kịch bản kiểm thử bằng Apache JMeter, cấu hình Thread Group, gửi yêu cầu HTTP GET và sử dụng View Results Tree cùng Aggregate Report để theo dõi kết quả.

Trong lần kiểm thử này, JMeter ghi nhận 2.217 yêu cầu, thời gian phản hồi trung bình 62 ms và tỷ lệ lỗi 0,00%. Kết quả cho thấy các yêu cầu được thực hiện thành công trong điều kiện thử nghiệm đã thiết lập.

Tuy nhiên, đây chỉ là kết quả của một kịch bản với 5 người dùng ảo trong 30 giây, chưa đủ để đánh giá khả năng chịu tải tối đa hoặc khẳng định hiệu năng của hệ thống trong mọi điều kiện.
