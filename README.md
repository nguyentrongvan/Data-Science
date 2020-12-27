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
- Dữ liệu thu thập được tổng cộng có 19411 mẫu và tổng số 31 thuộc tính.
- Dữ liệu được thu thập từ tin đăng mua bán giao dịch nhà đất của 19 quận thuộc Thành phố Hồ Chí Minh.
- Thuộc tính cần dự đoán là `house_type` - tức là `Loại nhà ở` với 4 giá trị bao gồm: 
  - Nhà mặt tiền, mặt phố.
  - Nhà phố liền kề.
  - Nhà ngõ, hẻm.
  - Nhà biệt thự.

### 5. Thuộc tính dữ liệu:
Dữ liệu thu thập được gồm 31 thuộc tính với ý nghĩa:
|Tên thuộc tính|Ý nghĩa|Kiểu dữ liệu|Giá trị|
|:----------:|:----------|:----------:|:----------|
|project_name|Tên dự án mua bán|Chuỗi ký tự|Ví dụ: |
|apartment_code|Mã căn hộ|Chuỗi ký tự|Ví dụ: |
|block_name|Tên của khu, phân lô cần giao dịch|Chuỗi ký tự|Ví dụ: |
|block_code|Mã của khu, phân lô cần giao dịch|Chuỗi ký tự|Ví dụ: |
|square|Diện tích đất (dùng cho mua bán đất)|Số thực|Ví dụ: $30 m^2$|
|square_area|Diện tích đất (dùng cho mua bán nhà)|Số thực|Ví dụ: $100 m^2$|
