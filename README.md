# Khoa học dữ liệu và Ứng dụng
### *Data science & Application*

## I. Thông tin sinh viên thực hiện:
|STT|MSSV|Họ và tên|
|:----------:|:---------:|:---------|
|1|1712202|Nguyễn Trọng Văn|
|2|1712449|Lê Đức Hòa|

## II. Thông tin đồ án:
### 1. Câu hỏi đặt ra:
***a)Vấn đề:***
- Dự đoán giá nhà là bài toán quen thuộc.
- Thông tin giá nhà thông qua nhiều thuộc tính: diện tích, phòng ngủ, loại nhà,...
- Ngược lại, người mua có thể biết được loại nhà nào có thể mua trong khả năng? (số tiền có, mong muốn vị trí, chiều dài, diện tích,...)

***b)Câu hỏi đặt ra:***
Có thể phân loại nhà ở (mặt tiền, ngõ hẻm,biệt thự, ...) theo các đặc điểm mua bán (diện tích, vị trí, giáthành, ...) hay không?

### 2. Ý nghĩa khi giải trả lời được câu hỏi:
- Người mua có thể biết được loại nhà ở mình có thể giao dịch với khả năng và mong muốn hiện có.
- Hỗ trợ tư vấn mua bán giao dịch nhà đất.
- Tự động phân loại nhà ở theo đặc điểm trên các website, hệ thống mua bán bất động sản.

### 3. Cách thức thu thập dữ liệu:
- Dữ liệu được thu thập bằng cách parse HMTL để tìm ra các trường thông tin cần thiết cho đồ án.
- Nguồn thu thập dữ liệu được lấy từ mục mua bán nhà đất, BĐS của website Chợ Tốt (https://www.chotot.com).
- File *CrawData.ipynb* là file code thực hiện thu thập dữ liệu.

### 4. Tổng quan dữ liệu thu thập:
- Dữ liệu thu thập được tổng cộng có 19411 mẫu và tổng số 30 thuộc tính.
- Dữ liệu được thu thập từ tin đăng mua bán giao dịch nhà đất của 19 quận thuộc Thành phố Hồ Chí Minh.
- Thuộc tính cần dự đoán là `house_type` - tức là `Loại nhà ở` với 4 giá trị bao gồm: 
  - Nhà mặt tiền, mặt phố.
  - Nhà phố liền kề.
  - Nhà ngõ, hẻm.
  - Nhà biệt thự.

### 5. Thuộc tính dữ liệu:
Dữ liệu thu thập được gồm 30 thuộc tính với ý nghĩa:
|Tên thuộc tính|Ý nghĩa|Kiểu dữ liệu|Giá trị|
|:----------:|:----------|:----------:|:----------|
|title|Chủ đề|Chuỗi ký tự| Ví dụ: Nhà phố cao cấp|
|address|Địa chỉ|Chuỗi ký tự|Ví dụ: Đường Nguyễn Văn Nguyễn, Phường Tân Định, Quận 1, Tp Hồ Chí Minh|
|project_name|Tên dự án mua bán|Chuỗi ký tự|Ví dụ: Vạn Xuân Đất Việt|
|apartment_code|Mã căn hộ|Chuỗi ký tự|Ví dụ: 88, 10|
|block_name|Tên của khu, phân lô cần giao dịch|Chuỗi ký tự|Ví dụ: |
|block_code|Mã của khu, phân lô cần giao dịch|Chuỗi ký tự|Ví dụ: |
|square|Diện tích đất (dùng cho mua bán đất)|Số thực|Ví dụ: 30 m2|
|square_area|Diện tích đất (dùng cho mua bán nhà)|Số thực|Ví dụ: 100 m2|
|square_in_use|Diện tích sử dụng (tổng diện tích nền được xây dựng)|Số thực| Ví dụ: 200 m2|
|bedroom|Số phòng ngủ có|Số nguyên|Ví dụ: 5 phòng, Nhiều hơn 10 phòng|
|wc|Số phòng vệ sinh có|Số nguyên|Ví dụ: 2 phòng, Nhiều hơn 6 phòng|
|num_floor|Tổng số tầng trong nhà|Số nguyên|Ví dụ: 1,2,10,...|
|floor|Tầng cần bán (nếu là chung cư)|Số nguyên|Ví dụ: 1,2,...|
|width|Chiều rộng khu dất|Số thực|Ví dụ: 2.5 m|
|height|Chiều dài khu đất|Số thực|Ví dụ: 4.5 m, 3 m|
|door|Hướng cửa chính|Chuỗi ký tự|Ví dụ: Tây-Nam, Bắc|
|balcony|Hướng ban công|Chuỗi ký tự|Ví dụ: Bắc, Đông Nam|
|estate_type|Loại hình đất|Chuỗi ký tự||
|office_type|Loại hình văn phòng|Chuỗi ký tự||
|apartment_type|Loại hình căn hộ|Chuỗi ký tự||
|certificates|Giấy tờ pháp lý|Chuỗi ký tự|Ví dụ: Đã có sổ, Đang chờ sổ|
|status|Tình trạng nhà|Chuỗi ký tự||
|furniture_status|Tình trạng nội thất|Chuỗi ký tự|Ví dụ: Bàn giao thô, Hoàn thiện cơ bản, Hoàn thiện đầy đủ,...|
|estate_status|Tình trạng bất động sản|Chuỗi ký tự|Ví dụ: Đang tranh chấp|
|apartment_specific|Đặc điểm căn hộ|Chuỗi ký tự||
|house_specific|Đặc điểm nhà ở|Chuỗi ký tự|Ví dụ: Hẻm xe hơi, Nở hậu,...|
|price_m2|Giá trên 1m2 đất|Số thực|Ví dụ: 10 triệu/m2|
|price_square|Giá bán 1 căn nhà|Số thực| Ví dụ: 10 tỷ - 100m2|
|_type_|Loại khác|||
|house_type|Loại nhà ở|Ví dụ: Nhà mặt tiền, mặt phố, Nhà biệt thự, Nhà phố liền kề, Nhà ngỏ, hẻm|

### 6. Tự đánh giá đồ án:

### 7. Phân công công việc:

### 8. Hướng dẫn chạy code:
