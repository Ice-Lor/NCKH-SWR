# Paper 04 Summary: Optimizing E-Commerce Product Classification Using Transfer Learning

## 1. Citation

* **Tên bài báo:** Optimizing E-Commerce Product Classification Using Transfer Learning[cite: 2]
* **Tác giả:** Rashmeet Kaur Khanuja[cite: 2]
* **Năm xuất bản:** 2019[cite: 2]
* **Nguồn phát hành:** San Jose State University, Master's Projects[cite: 2]
* **DOI / Link:** [10.31979/etd.egyw-ktc5](https://doi.org/10.31979/etd.egyw-ktc5)[cite: 2]

---

## 2. Problem Statement

Bài báo tập trung giải quyết các vấn đề cấp thiết trong việc phân loại danh mục hàng hóa khi thị trường thương mại điện tử bùng nổ:
* **Hạn chế của phân loại văn bản:** Việc phân loại hoàn toàn dựa trên văn bản (tiêu đề, mô tả) dẫn đến nhiều sai lệch, nguyên nhân do các nhà bán hàng (merchants) có hệ thống phân loại riêng, sử dụng từ vựng thiếu nhất quán hoặc cố tình thêm từ khóa không liên quan để tăng hiển thị.[cite: 2]
* **Tác động tiêu cực đến trải nghiệm:** Sản phẩm bị phân loại sai lệch làm hiển thị các kết quả tìm kiếm không liên quan, gây ảnh hưởng trực tiếp đến trải nghiệm điều hướng của người dùng trên website.[cite: 2]
* **Hạn chế của mạng CNN truyền thống:** Sử dụng hình ảnh thay thế văn bản đem lại độ chính xác cao hơn, nhưng huấn luyện một mạng nơ-ron tích chập (CNN) truyền thống từ đầu rất tốn kém về thời gian, chi phí tính toán và dễ bị học vẹt (overfitting) khi thiếu dữ liệu mẫu.[cite: 2]
* **Mục tiêu cốt lõi:** Đề xuất kỹ thuật Học chuyển giao (Transfer Learning) để tự động hóa việc phân loại hình ảnh sản phẩm, nhằm duy trì độ chính xác của mạng CNN đồng thời giảm thiểu đáng kể thời gian huấn luyện.[cite: 2]

---

## 3. Proposed Method

Nghiên cứu ứng dụng phương pháp Học chuyển giao dựa trên kiến trúc mạng **VGG-16** đã được huấn luyện trước (pre-trained).[cite: 2]

### Quy trình xử lý và thiết kế mạng:
1.  **Trích xuất đặc trưng (Feature Extraction):** Loại bỏ các lớp phân loại ở tầng cuối (top layers) của mạng VGG-16.[cite: 2] Giữ nguyên và đóng băng (freeze) 5 khối lớp tích chập và gộp (convolutional and max pooling layers) đầu tiên để mạng đóng vai trò tự động trích xuất các đặc trưng hình ảnh.[cite: 2]
2.  **Thiết kế bộ phân loại mới:** Đầu ra của các lớp trích xuất đặc trưng được đưa qua lớp làm phẳng (Flatten), tiếp nối bằng lớp Dense với hàm kích hoạt ReLU, một lớp Dropout (tỷ lệ 0.5) để ngăn chặn overfitting, và kết thúc bằng lớp Dense sử dụng hàm kích hoạt Sigmoid.[cite: 2]
3.  **Chiến lược Phân loại "Một đấu Tất cả" (One versus All):** Do việc huấn luyện phân loại đa lớp (multi-class) cùng lúc chỉ đạt độ chính xác 35.9%, nghiên cứu chuyển sang huấn luyện các mô hình phân loại nhị phân độc lập cho từng danh mục riêng biệt (ví dụ: gán nhãn 0 cho danh mục Appliances và nhãn 1 cho tất cả các hình ảnh còn lại).[cite: 2]

---

## 4. Dataset Characteristics

Nghiên cứu sử dụng nguồn dữ liệu kết hợp để phục vụ phương pháp Học chuyển giao:

### Thông số kỹ thuật chi tiết của tập dữ liệu

| Thuộc tính dữ liệu | Chi tiết thông số cấu trúc |
| :--- | :--- |
| **Tập dữ liệu Nguồn (Source)** | Sử dụng tập dữ liệu **ImageNet** (chứa hơn 1.2 triệu ảnh huấn luyện thuộc 1000 danh mục) để cung cấp trọng số tiền huấn luyện cho mạng VGG-16.[cite: 2] |
| **Tập dữ liệu Đích (Target)** | Thu thập tự động từ một nền tảng thương mại điện tử bằng công cụ web crawler (sử dụng Python, Selenium và BeautifulSoup).[cite: 2] |
| **Quy mô và Phân chia** | Tổng cộng khoảng **17.500** hình ảnh sản phẩm thực tế.[cite: 2]<br>• Trích xuất khoảng **900 mẫu** cho mỗi danh mục để làm tập kiểm thử (Test data).[cite: 2]<br>• Phần còn lại chia cho tập huấn luyện (Training) và kiểm định (Validation).[cite: 2] |
| **Số lượng danh mục** | Gồm 5 danh mục tổng quát (Ví dụ: Appliances, Electronics, Furniture, Toys...).[cite: 2] |

---

## 5. Evaluation Metrics

Quá trình kiểm thử mô hình dựa trên các tiêu chí cốt lõi:
* **Độ chính xác (Accuracy):** Tỷ lệ dự đoán đúng trên tập huấn luyện (Train Accuracy) và tập kiểm định (Validation Accuracy).[cite: 2]
* **Hàm mất mát (Loss Value):** Đo lường sai số dự đoán thông qua hàm Binary Cross-entropy.[cite: 2]
* **Thời gian tính toán:** Đo lường sự tối ưu về thời gian huấn luyện (Training time) giữa mô hình Transfer Learning so với CNN truyền thống trên cùng một cấu hình phần cứng.[cite: 2]

---

## 6. Experimental Results

Thực nghiệm đã chứng minh ưu điểm vượt trội của phương pháp Transfer Learning so với thiết kế mạng CNN truyền thống:

### Các kết luận thực nghiệm chính:
* **Hiệu năng của CNN truyền thống:** Mất hơn 3 giờ để huấn luyện trên một tập dữ liệu nhỏ nhưng chỉ đạt mức chính xác 79%.[cite: 2] Đồ thị hiển thị rõ hiện tượng Overfitting khi độ chính xác huấn luyện lên tới 90% nhưng độ chính xác kiểm định lại sụt giảm nghiêm trọng.[cite: 2]
* **Hiệu năng của Transfer Learning (Đa lớp):** Tốc độ huấn luyện giảm đột phá xuống chỉ còn khoảng **16.96 phút** trên cùng lượng dữ liệu, với độ chính xác trung bình đạt 85%.[cite: 2]
* **Sức mạnh của chiến lược "One vs All":** Khi huấn luyện mô hình nhị phân cho từng danh mục riêng lẻ, hiệu năng được cải thiện rõ rệt với độ chính xác trung bình lên tới **89%**.[cite: 2]

---

## 7. Limitations & Research Gaps

Dù giải quyết tốt bài toán tối ưu chi phí, bài báo vẫn tồn tại những rào cản khi ứng dụng vào môi trường dữ liệu quy mô lớn:
* **Phân loại ở cấp độ vĩ mô:** Nghiên cứu chỉ thử nghiệm trên 5 danh mục sản phẩm rất rộng (macro-categories như Electronics, Appliances).[cite: 2] Việc không mở rộng phân loại xuống các danh mục con (sub-categories như Laptops, Tablets) làm giảm tính khả thi ứng dụng thực tế trên website.[cite: 2]
* **Rào cản về mở rộng hệ thống:** Việc áp dụng chiến lược "Một đấu Tất cả" đòi hỏi phải huấn luyện và duy trì số lượng mô hình phân loại bằng đúng số lượng danh mục hiện có.[cite: 2] Điều này sẽ gây quá tải tài nguyên quản lý khi số lượng danh mục của hệ thống lên đến hàng ngàn.

---

## 8. Relevance to Our Topic

Nghiên cứu mang lại luận điểm kỹ thuật quan trọng để thiết kế hoàn chỉnh hệ thống dữ liệu tự động hoá cho bài Lab lớn. Cấu trúc mô hình Transfer Learning giải quyết bài toán làm sạch dữ liệu hình ảnh ngay từ khâu đầu vào:
* Với vai trò phân chia công việc cho 5 thành viên trong nhóm, quy trình có thể được rạch ròi thành hai nhánh chính: một nhóm phụ trách pipeline xử lý hình ảnh dựa trên kiến trúc VGG-16, nhóm còn lại tập trung xây dựng sơ đồ thực thể mối kết hợp (ERD).
* Thay vì nhập tay danh mục cho từng bức ảnh tải lên, hệ thống sẽ tự động phân loại, sau đó gọi trực tiếp các stored procedures trong SQL Server để thực thi lệnh `INSERT` dữ liệu một cách nhất quán. Nắm bắt được công nghệ nhận diện tự động này sẽ là điểm nhấn quan trọng giúp nhóm hoàn thiện xuất sắc report 5 – báo cáo tổng kết cuối cùng của toàn bộ dự án.

---

## 9. Possible Improvements & Future Extensions

Dựa trên đề xuất của bài báo, nhóm có thể thực thi các hướng mở rộng kỹ thuật chuyên sâu để tích hợp trực tiếp vào cấu trúc cơ sở dữ liệu:

### Kế hoạch cải tiến và mở rộng giải pháp của nhóm

| Khoảng trống của bài báo | Giải pháp cải tiến cụ thể của nhóm | Kỹ thuật triển khai dự kiến |
| :--- | :--- | :--- |
| **Chỉ phân loại ở cấp độ danh mục lớn (Macro-categories)**[cite: 2] | Mở rộng mô hình để phân loại chính xác các danh mục con (Sub-categories), đi sâu vào cấu trúc phân cấp đa tầng của các ngành hàng thực tế.[cite: 2] | Tối ưu hóa cấu trúc CSDL SQL Server bằng thiết kế bảng tự tham chiếu (Self-referencing Category Table). Dùng các lệnh joins và subqueries phức tạp để thiết lập logic tự động nối dữ liệu từ mô hình AI vào đúng node con tương ứng. |
| **Chiến lược "One vs All" sinh ra quá nhiều mô hình**[cite: 2] | Khắc phục giới hạn bằng cách tích hợp mô hình phân loại đa lớp (Multi-class/Multi-label) thống nhất có độ ổn định cao hơn mô hình cơ bản trong báo cáo. | Thử nghiệm loại bỏ thiết kế nhiều hàm Sigmoid riêng biệt, thay bằng lớp Softmax hoặc sử dụng kiến trúc Transfer Learning tiên tiến hơn (như ResNet) để hội tụ tất cả danh mục vào một mô hình duy nhất. |
| **Chưa tận dụng triệt để bộ trích xuất đặc trưng** | Tái sử dụng các đặc trưng hình ảnh (Feature Vectors) để phát triển hệ thống gợi ý sản phẩm dựa trên độ tương đồng (Near matching recommender).[cite: 2] | Lưu trữ các chuỗi vector đặc trưng từ lớp áp chót của VGG-16 vào các trường dữ liệu thích hợp. Viết các thủ tục truy vấn nâng cao để tính toán khoảng cách vector, từ đó hiển thị danh sách sản phẩm tương tự khi người dùng đang xem một mặt hàng. |