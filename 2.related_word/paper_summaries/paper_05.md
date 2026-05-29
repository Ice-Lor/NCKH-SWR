# Paper 03 Summary: An Image-based Transfer Learning Framework for Classification of E-Commerce Products

## 1. Citation

* **Tên bài báo:** An Image-based Transfer Learning Framework for Classification of E-Commerce Products
* **Tác giả:** Vrushali Atul Surve, Pramod Pathak, Mohammed Hasanuzzaman, Rejwanul Haque, Paul Stynes
* **Năm xuất bản:** 2022
* **Nguồn phát hành:** ICDLT '22: Proceedings of the 2022 6th International Conference on Deep Learning Technologies
* **DOI / Link:** [10.1145/3556677.3556689](https://doi.org/10.1145/3556677.3556689)

---

## 2. Problem Statement

Nghiên cứu tập trung giải quyết bài toán cốt lõi trong hệ thống quản lý danh mục của các nền tảng thương mại điện tử:
* **Thách thức của thương mại điện tử:** Việc phân loại chính xác một sản phẩm từ hàng trăm danh mục (ví dụ: một đôi giày thể thao Nike Air Max phải được tự động xếp đúng vào danh mục "Giày nam") tốn rất nhiều thời gian và nguồn lực nếu xử lý bằng phương pháp thủ công hoặc hệ thống phân loại cũ.
* **Tác động của hình ảnh sai lệch:** Hình ảnh đóng vai trò sống còn trong việc điều hướng người dùng. Những hình ảnh bị phân loại sai hoặc gây hiểu lầm sẽ phá vỡ tính logic của hệ thống tìm kiếm, làm người dùng thất vọng và rời bỏ nền tảng.
* **Mục tiêu nghiên cứu:** Đề xuất một Khung học chuyển giao xử lý ảnh (Image-based Transfer Learning Framework) nhằm tự động nhận diện và phân loại hình ảnh sản phẩm vào đúng danh mục trong khoảng thời gian ngắn nhất, trong khi vẫn duy trì hiệu suất phân loại cao.

---

## 3. Proposed Method

Nghiên cứu đề xuất giải pháp kết hợp giữa các thuật toán xử lý ảnh truyền thống với sức mạnh của kỹ thuật **Học chuyển giao (Transfer Learning)**:
* Khung làm việc (Framework) tiến hành đối chuẩn (benchmark) toàn diện giữa một mạng nơ-ron tích chập xây từ đầu (Traditional CNN) với 4 kiến trúc Học chuyển giao nổi tiếng bao gồm: **VGG-19, Inception V3, ResNet50 và MobileNet**.
* Kiến trúc của hệ thống tận dụng các bộ lọc đặc trưng đã được học sẵn, kết nối với các lớp phân loại kết nối đầy đủ (Fully Connected layers) và thuật toán Softmax ở tầng cuối cùng để nhận dạng, đối chiếu và đưa ra dự đoán nhãn danh mục cho hình ảnh.

---

## 4. Dataset Characteristics

Để phục vụ cho mô hình đánh giá và tinh chỉnh, nghiên cứu sử dụng tập dữ liệu phân tầng:
* **Nguồn tri thức cốt lõi:** Kế thừa bộ trọng số đã được huấn luyện trước trên tập dữ liệu nhận diện ảnh tĩnh khổng lồ **ImageNet**.
* **Dữ liệu thực nghiệm (Dataset-2):** Phục vụ cho mục tiêu thương mại điện tử, nhóm tác giả đã tự động thu thập (web scraping) một tập dữ liệu gồm **15.000 hình ảnh sản phẩm** trực tiếp từ nhiều nền tảng và môi trường bối cảnh trang web đa dạng trên internet. 

---

## 5. Evaluation Metrics

Khung đánh giá các mô hình trong hệ thống dựa trên hai chỉ số đo lường thực tiễn:
* **Độ chính xác (Accuracy / Precision / Recall / F1-Score):** Tỷ lệ dự đoán đúng nhãn danh mục của hình ảnh, đồng thời đánh giá khả năng mô hình tự động phân tích độ chính xác của hình ảnh giống như cách một người dùng thông thường nhìn nhận.
* **Thời gian dự đoán (Timing):** Tốc độ phản hồi (tính bằng giây) của mô hình từ khi nhận đầu vào đến khi trả ra kết quả danh mục.

---

## 6. Experimental Results

Thực nghiệm đã chứng minh ưu thế của việc tận dụng Transfer Learning cho bài toán phân loại thương mại điện tử:
* Các mô hình Học chuyển giao vượt trội hơn hẳn so với CNN truyền thống ở cả hai khía cạnh là thời gian đào tạo và độ nhạy bén phân loại.
* Đáng chú ý nhất, mô hình **Inception V3** cung cấp hiệu suất tổng thể xuất sắc nhất.
* Cụ thể, Inception V3 đạt được độ chính xác lên đến **85%** và thời gian để xử lý phân loại một hình ảnh đầu vào chỉ mất vỏn vẹn **0.10 giây**.

---

## 7. Limitations & Research Gaps

Mặc dù giải quyết rất tốt bài toán về tốc độ, nhưng nghiên cứu vẫn còn một số điểm giới hạn:
* **Rủi ro ở mức chính xác 85%:** Dù thời gian cực nhanh (0.10s), nhưng mức chính xác 85% đồng nghĩa hệ thống vẫn có 15% rủi ro dự đoán sai. Khi ánh xạ vào một nền tảng thực tế có hàng triệu lệnh tạo sản phẩm, tỷ lệ sai số 15% này sẽ tạo ra lượng dữ liệu rác không nhỏ.
* **Tính đa dạng dữ liệu cào (Scraping data):** 15.000 ảnh lấy từ web chưa phản ánh đầy đủ thách thức của nhiễu ảnh thực tế (chẳng hạn như ảnh người dùng chụp bị khuất góc, độ phân giải kém, hoặc một khung hình xuất hiện đan xen nhiều loại sản phẩm khác nhau).

---

## 8. Relevance to Our Topic

Nghiên cứu này đem lại những minh chứng khoa học và thông số kỹ thuật cốt lõi giúp hoàn thiện toàn diện **Report 5** (báo cáo cuối cùng) trong bài Lab lớn môn Cơ sở dữ liệu của nhóm 5 người.
* **Tối ưu hóa thời gian thực (Real-time optimization):** Việc bài báo chứng minh Inception V3 chỉ mất **0.10 giây** để xử lý một hình ảnh là một điểm cộng rất lớn. Khi tích hợp module nhận diện này vào kiến trúc backend (Java), tốc độ phản hồi 0.10s đảm bảo hệ thống không bị nghẽn luồng truy vấn. Các lệnh kết nối qua JDBC để `INSERT` hoặc `UPDATE` dữ liệu vào SQL Server sẽ được thực thi gần như tức thời khi quản trị viên tải ảnh lên.
* **Bảo vệ luận điểm kiến trúc hệ thống:** Nhóm có thể trực tiếp trích dẫn kết quả của báo cáo này làm cơ sở vững chắc để lập luận việc ưu tiên tích hợp các mô hình tinh gọn như Inception V3 hoặc MobileNet, thay vì tiêu tốn tài nguyên quản trị và phần cứng để phát triển lại mô hình học sâu từ con số không.

---

## 9. Possible Improvements & Future Extensions

Để khắc phục các khoảng trống của bài báo và nâng cấp mô hình cho tương thích hoàn toàn với cấu trúc cơ sở dữ liệu thực tế mà nhóm đang thiết kế, có thể đề xuất:

### Kế hoạch cải tiến và mở rộng giải pháp của nhóm

| Khoảng trống của bài báo | Giải pháp cải tiến cụ thể của nhóm | Kỹ thuật triển khai dự kiến |
| :--- | :--- | :--- |
| **Độ chính xác mới dừng ở 85%** | Xây dựng luồng xác thực dữ liệu (Data Validation) lai giữa AI và con người để kiểm soát 15% sai sót có thể xâm nhập vào CSDL. | Thiết lập Trigger hoặc Stored Procedure trong SQL Server: Nếu hàm Softmax trả về Confidence Score < 90%, luồng Java sẽ đưa bản ghi đó vào bảng tạm (Staging Table) để trưởng nhóm hoặc quản trị viên duyệt thủ công trước khi chuyển sang bảng thực thể chính. |
| **Dữ liệu cào từ web (Scraping) thường có nhiễu** | Làm sạch dữ liệu trước khi lưu trữ URL và ghi nhận tham chiếu file ảnh vào hệ thống. | Thiết kế thuật toán tiền xử lý trên tầng Backend để tự động quét, loại bỏ các ảnh trùng lặp (dựa trên thuật toán Hashing MD5/SHA) hoặc ảnh bị lỗi định dạng từ client. |
| **Đánh giá mới dừng ở mức so sánh học sâu** | Tích hợp thêm các phương pháp thống kê toán học để quá trình kiểm định chất lượng phân loại của mô hình ở Report 5 trở nên chặt chẽ và học thuật hơn. | Sử dụng các kiến thức xác suất thống kê và toán rời rạc (chẳng hạn như Phân phối chuẩn hóa, kiểm định giả thuyết - Hypothesis Testing) để đo lường tính ổn định của độ chính xác và phương sai trên nhiều tập mẫu dữ liệu khác nhau. |