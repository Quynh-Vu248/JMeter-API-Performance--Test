# BÁO CÁO THỰC HÀNH APACHE JMETER

## 1. Giới thiệu

### 1.1. Mục tiêu

Bài thực hành nhằm tìm hiểu và sử dụng Apache JMeter để kiểm thử hiệu năng API. Qua quá trình thực hiện, người học làm quen với việc xây dựng kịch bản kiểm thử, gửi HTTP Request, theo dõi phản hồi và phân tích các chỉ số hiệu năng.

### 1.2. Công cụ sử dụng

- Công cụ kiểm thử: Apache JMeter 5.6.3.
- Hệ điều hành: Windows.
- Giao thức: HTTPS.
- Phương thức HTTP: GET.
- API thực hành: https://jsonplaceholder.typicode.com/posts/1.

## 2. Tìm hiểu Apache JMeter

Apache JMeter là công cụ mã nguồn mở được sử dụng để kiểm thử hiệu năng và tải của ứng dụng web, API và các hệ thống hỗ trợ giao thức phù hợp.

Một số thành phần được sử dụng trong bài thực hành:

- **Test Plan:** Kế hoạch kiểm thử tổng thể.
- **Thread Group:** Cấu hình số người dùng mô phỏng, thời gian khởi chạy và số vòng lặp.
- **HTTP Request:** Gửi yêu cầu HTTP đến API.
- **View Results Tree:** Xem kết quả và phản hồi của từng yêu cầu.
- **Summary Report:** Tổng hợp các chỉ số hiệu năng.

### Minh chứng 1: Giao diện JMeter

<img width="1147" height="610" alt="image" src="https://github.com/user-attachments/assets/a25fcdad-615e-4225-a54d-387d3c840011" />


## 3. Xây dựng kịch bản kiểm thử

### 3.1. Cấu hình Thread Group

Tạo Thread Group có tên `API Test Users` để thiết lập các tham số mô phỏng người dùng.

| Thông số | Giá trị |
|---|---|
| Number of Threads | 5 |
| Ramp-up Period | 5 giây |
| Loop Count | 5 |


### Minh chứng 2: Cấu hình Thread Group

<img width="1151" height="605" alt="image" src="https://github.com/user-attachments/assets/694cb3bd-287d-4d7a-a938-1baf634626d4" />

### 3.2. Cấu hình HTTP Request

Bài thực hành sử dụng yêu cầu GET để truy xuất thông tin bài viết từ API JSONPlaceholder.

| Thông số | Giá trị |
|---|---|
| Name | GET Single Post |
| Protocol | HTTPS |
| Server Name or IP | jsonplaceholder.typicode.com |
| Method | GET |
| Path | /posts/1 |

API trả về dữ liệu bài viết dưới định dạng JSON.

### Minh chứng 3: Cấu hình HTTP Request

![Cấu hình HTTP Request](screenshots/03-http-request.png)

## 4. Thực hiện kiểm thử

Sau khi cấu hình Test Plan, người thực hiện lưu kịch bản và nhấn Start để chạy kiểm thử.

View Results Tree được sử dụng để theo dõi từng yêu cầu, kiểm tra mã phản hồi và xem dữ liệu JSON trả về. Summary Report được sử dụng để tổng hợp kết quả sau khi chạy.

### Minh chứng 4: Kết quả phản hồi API

<img width="1337" height="729" alt="image" src="https://github.com/user-attachments/assets/a25a4105-3ff7-4cff-821b-a4d5f1732251" />

## 5. Kết quả kiểm thử

Dựa trên Summary Report của lần chạy thực tế, kết quả ghi nhận như sau:

| Chỉ số | Kết quả |
|---|---:|
| Tổng số mẫu (Samples) | 50 |
| Thời gian phản hồi trung bình (Average) | 181 ms |
| Thời gian phản hồi nhỏ nhất (Min) | 55 ms |
| Thời gian phản hồi lớn nhất (Max) | 1.210 ms |
| Độ lệch chuẩn (Std. Dev.) | 243,23 ms |
| Tỷ lệ lỗi (Error %) | 0,00% |

### Minh chứng 5: Summary Report

<img width="1270" height="610" alt="image" src="https://github.com/user-attachments/assets/1c614909-f037-465d-9a55-0ce6b5c34799" />


### 5.1. Nhận xét kết quả

- JMeter ghi nhận 50 mẫu yêu cầu trong lần chạy được báo cáo.
- Thời gian phản hồi trung bình là 181 ms.
- Thời gian phản hồi nhỏ nhất là 55 ms và lớn nhất là 1.210 ms.
- Tỷ lệ lỗi hiển thị là 0,00%, nghĩa là không có mẫu nào bị JMeter đánh dấu lỗi trong lần chạy này.
- Độ lệch chuẩn là 243,23 ms, cho thấy thời gian phản hồi có sự dao động giữa các mẫu.

### 5.2. Đánh giá

Trong lần kiểm thử này, JMeter đã thực hiện các yêu cầu và ghi nhận kết quả tổng hợp. Tỷ lệ lỗi 0,00% là kết quả tích cực đối với kịch bản thực hành quy mô nhỏ.

Tuy nhiên, kết quả chỉ phản ánh lần chạy và điều kiện thử nghiệm cụ thể. Chưa thể kết luận về khả năng chịu tải tối đa của API từ bài thực hành này.

## 6. Kết luận

Qua bài thực hành, người học đã làm quen với giao diện Apache JMeter, tạo Test Plan, cấu hình Thread Group, gửi HTTP Request và sử dụng Listener để theo dõi, phân tích kết quả.

Bài thực hành giúp củng cố kiến thức cơ bản về kiểm thử hiệu năng API và tạo nền tảng để tìm hiểu thêm về kiểm thử tải, kiểm thử sức chịu tải và báo cáo hiệu năng nâng cao.

## 7. Tài liệu tham khảo

1. Apache JMeter: https://jmeter.apache.org/
2. Apache JMeter Getting Started: https://jmeter.apache.org/usermanual/get-started.html
3. Apache JMeter Building a Test Plan: https://jmeter.apache.org/usermanual/build-test-plan.html
4. JSONPlaceholder: https://jsonplaceholder.typicode.com/

## 8. Tệp sản phẩm

- `JMeter_API_Test.jmx`: Kịch bản kiểm thử được tạo bằng Apache JMeter.
- `screenshots/`: Thư mục chứa các ảnh minh chứng thực hiện bài tập.
- `README.md`: Báo cáo mô tả quá trình thực hiện và kết quả kiểm thử.
