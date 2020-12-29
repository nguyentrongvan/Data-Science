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
- Dữ liệu thu thập được tổng cộng có 19,411 mẫu và tổng số 30 thuộc tính.
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
|block_name|Tên của khu, phân lô cần giao dịch|Chuỗi ký tự|Ví dụ: KDC Vĩnh Loccj 3|
|block_code|Mã của khu, phân lô cần giao dịch|Chuỗi ký tự|Ví dụ: D3, B2|
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
|estate_type|Loại hình đất|Chuỗi ký tự|Ví dụ: Đất thổ cư, Đất công nghiệp|
|office_type|Loại hình văn phòng|Chuỗi ký tự|Ví dụ: Mặt bằng kinh doanh|
|apartment_type|Loại hình căn hộ|Chuỗi ký tự|Ví dụ: Chung cư|
|certificates|Giấy tờ pháp lý|Chuỗi ký tự|Ví dụ: Đã có sổ, Đang chờ sổ|
|status|Tình trạng nhà|_|_|
|furniture_status|Tình trạng nội thất|Chuỗi ký tự|Ví dụ: Bàn giao thô, Hoàn thiện cơ bản, Hoàn thiện đầy đủ,...|
|estate_status|Tình trạng bất động sản|Chuỗi ký tự|Ví dụ: Đang tranh chấp|
|apartment_specific|Đặc điểm căn hộ|Chuỗi ký tự|Ví dụ: Căn góc|
|house_specific|Đặc điểm nhà ở|Chuỗi ký tự|Ví dụ: Hẻm xe hơi, Nở hậu,...|
|price_m2|Giá trên 1m2 đất|Số thực|Ví dụ: 10 triệu/m2|
|price_square|Giá bán 1 căn nhà|Số thực| Ví dụ: 10 tỷ - 100m2|
|_type_|Loại khác|_|_|
|house_type|Loại nhà ở|Chuỗi ký tự|Ví dụ: Nhà mặt tiền, mặt phố, Nhà biệt thự, Nhà phố liền kề, Nhà ngỏ, hẻm|
*(Một số trường thuộc tính không xác định được đánh dấu bằng _)*
### 6. Tự đánh giá đồ án:
***Nhận xét:***
- Đồ án hoàn thành tốt và đúng thời gian quy định.
- Công việc được phân công hợp lý rõ ràng.
- Dữ liệu thu thập được phục vụ khá tốt cho quá trình thực hiện đồ án, số lượng mẫu thu thập nhiều hơn so với mục tiêu ban đầu (mục tiêu được 10,000 mẫu, tổng thu thập được 19,411 mẫu). Các trường thuộc tính dữ liệu thu thập được nhiều hơn sau khi tiến hành parse HTML so với lúc ban đầu quan sát các trường thông tin có trên website.
- Kết quả thu được cuối cùng đạt được 80-90% mục tiêu đề ra là có thể mô hình hóa được dữ liệu để dự đoán thuộc tính lớp.
- Trả lời được cho câu hỏi đặt ra.

***Hạn chế:***
- Việc hiểu dữ liệu để tiến hành thu thập mất khá nhiều thời gian.
- Quá trình thu thập dữ liệu và tiền xử lý gặp nhiều khó khăn khi không kiểm soát được phân bố các giá trị mong muốn -> Tạo ra sự chênh lệch giá trị.

***Đề xuất:***
- Để có thể cải thiện tốt hơn cho mô hình dự đoán, cần có thêm dữ liệu đa dạng hơn (quy mô dữ liệu hiện giờ chỉ gói gọn ở khu vực TP.HCM các quận) và phân bố dữ liệu hợp lý hơn.
- Nếu dữ liệu thu thập đủ lớn và đủ tài nguyên sử dụng, có thể thiết kế các kiến trúc mạng học sâu phù hợp hoặc kết hợp các phương pháp rút trích đặc trưng khác nhau để tạo ra những đặc trưng tốt hơn cho quá trình học.

### 7. Phân công công việc:
|STT|Tên công việc|Phân công|
|:----------:|:----------:|:----------:|
|1|Đặt vấn đề, suy nghĩ câu hỏi, tìm nguồn dữ liệu|Nguyễn Trọng Văn, Lê Đức Hòa|
|2|Xác định các trường thuộc tính cần thiết và liên quan cho việc thu thập|Nguyễn Trọng Văn|
|3|Viết chương trình Parse HTML và tiến hành thu thập dữ liệu|Lê Đức Hòa|
|4|Quan sát dữ liệu thu thập được phân tích, thực hiền tiền xử lý: xóa trùng lắp, rời rạc hóa, gán nhãn|Nguyễn Trọng Văn|
|5|Tiền xử lý dữ liệu: điền rỗng, chuẩn hóa dữ liệu số|Lê Đức Hòa|
|6|Trực quan hóa dữ liệu, nhận xét|Nguyễn Trọng Văn|
|7|Thực hiện upsampling dữ liệu bị lệch, chuẩn hóa dữ liệu chuẩn bị cho quá trình học|Lê Đức Hòa|
|8|Lựa chọn mô hình học, đánh giá kết quả thu được, trực quan độ lỗi, đánh giá + kết luận|Nguyễn Trọng Văn, Lê Đức Hòa|

### 8. Hướng dẫn chạy code:
Cấu trúc code chia làm 3 file:
- ***CrawlData.ipynb***: File notebook chứa code thực thi thu thập dữ liệu. Để chạy code tải phiên bản chomredrive phù hợp với hệ đêìu hành sử dụng đẻ cùng thư mục với file notebook. Dùng jupyter-lab (hoặc jupyter-notebook) để mở file và chọn *Run -> Run All* hoặc *Kernel -> Restart Kernel and Run All*.
- ***DataPreprocessing.ipynb***: File notebook thực hiện phân tích, tiền xử lý và trực quan hóa dữ liệu. Dùng jupyter-lab (hoặc jupyter-notebook) để mở file và chọn *Run -> Run All* hoặc *Kernel -> Restart Kernel and Run All*.
- ***ModelPrediction.ipynb***: File notebook thực thi chuẩn bị dữ liệu cho quá trình học, các model được lựa chọn, kết quả thu được và kết luận. Dùng jupyter-lab (hoặc jupyter-notebook) để mở file và chọn *Run -> Run All* hoặc *Kernel -> Restart Kernel and Run All*.

**Lưu ý**: *Một số phần của các file có thể có thời gian chạy hơi lâu do quá trình thu thập dữ liệu nhiều, xử lý nhiều dòng dữ liệu, các mô hình chạy nhiều tham số,...*

Dữ liệu được thu thập lưu trữ trong thư mực Data với tổ chức:
Data:
|____Crawl: chứa dữ liệu thô khi mới được thu thập về.
|____Normal:
     |____Data.csv: data sau khi ghép các file thô lại. (thu thập từng file nhỏ rồi ghép lại thành file lớn)
     |____data_house.csv: dữ liệu nhà được lọc lại.
|____Preprocessing:
     |____preprocessing_data.csv: dữ liệu sau khi được tiền xử lý. 
