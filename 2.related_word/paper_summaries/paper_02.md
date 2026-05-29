# Paper 02 Summary: E-Commerce Product Image Classification using Transfer Learning

## 1. Citation

* **Tên bài báo:** E-Commerce Product Image Classification using Transfer Learning
* **Tác giả:** Bineet Kumar Jha, Sivasankari G.G, Venugopal K. R
* **Năm xuất bản:** 2021
* **Nguồn phát hành:** 2021 5th International Conference on Computing Methodologies and Communication (ICCMC)
* **DOI / Link:** [10.1109/ICCMC51019.2021.9418371](https://doi.org/10.1109/ICCMC51019.2021.9418371)

---

## 2. Problem Statement

Bài báo tập trung giải quyết các thách thức lớn trong khâu vận hành và quản lý của ngành thương mại điện tử (E-Commerce) hiện đại:
* **Sự bùng nổ dữ liệu hình ảnh:** Số lượng sản phẩm trên các sàn thương mại điện tử tăng trưởng theo cấp số nhân. Việc phân loại, gán nhãn thủ công hoặc sử dụng quy trình truyền thống tiêu tốn quá nhiều thời gian, chi phí và dễ sai sót.
* **Hạn chế tính toán của mạng CNN truyền thống:** Việc xây dựng và huấn luyện một mạng nơ-ron tích chập từ đầu (Train from Scratch) đòi hỏi tài nguyên phần cứng (GPU/CPU) cực lớn, thời gian hội tụ lâu và yêu cầu tập dữ liệu khổng lồ để tránh hiện tượng học vẹt (Overfitting).
* **Mục tiêu cốt lõi:** Đề xuất một giải pháp tự động hóa quá trình nhận diện danh mục sản phẩm có độ chính xác cao, tốc độ xử lý nhanh và tối ưu chi phí tính toán, phục vụ hiệu quả cho các tính năng như tìm kiếm bằng hình ảnh (Visual Search) và gợi ý sản phẩm thông minh.

---

## 3. Proposed Method

Nghiên cứu đề xuất ứng dụng phương pháp **Học chuyển giao (Transfer Learning)** bằng cách kế thừa tri thức (trọng số đã tối ưu) từ các mô hình học sâu (Deep Learning) mạnh mẽ được huấn luyện trước trên tập dữ liệu quy mô lớn ImageNet.

### Quy trình xử lý gồm 3 giai đoạn:
1.  **Tiền xử lý (Pre-processing):** Chuẩn hóa kích thước hình ảnh đầu vào và xử lý các giá trị pixel để đảm bảo tính đồng bộ trước khi đưa vào mạng nơ-ron.
2.  **Trích xuất đặc trưng (Feature Extraction):** Đóng băng (Freeze) các lớp tích chập sâu của các mô hình tiền huấn luyện để trích xuất tự động các đặc trưng hình học, đường nét, khối hình từ ảnh sản phẩm. Các kiến trúc được thử nghiệm bao gồm **VGG-19** và **Inception V3**.
3.  **Phân loại (Classification) & Tinh chỉnh (Fine-tuning):** Thay thế và huấn luyện lại các lớp kết nối đầy đủ (Fully Connected Layers) ở cuối mạng để phân loại chính xác các danh mục sản phẩm mục tiêu.

### So sánh đặc điểm kiến trúc mạng trong nghiên cứu

| Tiêu chí so sánh | Mạng CNN Xây từ đầu (Baseline) | Kiến trúc VGG-19 | Kiến trúc Inception V3 |
| :--- | :--- | :--- | :--- |
| **Khởi tạo trọng số** | Ngẫu nhiên (Random Initialization) | Kế thừa trọng số tiền huấn luyện (ImageNet) | Kế thừa trọng số tiền huấn luyện (ImageNet) |
| **Độ sâu kiến trúc** | Nông, cấu hình thủ công tùy biến | Sâu (19 lớp), cấu trúc tuần tự tuyến tính | Rất sâu, cấu trúc bất đối xứng đa nhánh (Inception Modules) |
| **Đặc trưng trích xuất** | Học từ số không, hiệu quả thấp với data nhỏ | Khả năng trích xuất hình khối cơ bản mạnh mẽ | Trích xuất đặc trưng đa quy mô (Multi-scale features) tốt |
| **Tốc độ huấn luyện** | Rất chậm để đạt độ chính xác tối ưu | Nhanh hơn nhờ đóng băng trọng số | Tối ưu hóa bộ nhớ và tốc độ hội tụ vượt trội |

---

## 4. Dataset Characteristics

Nghiên cứu sử dụng tập dữ liệu chuẩn **Fashion MNIST** (được thu thập từ nền tảng Kaggle) làm benchmark để đánh giá hiệu năng thuật toán phân loại.

### Thông số kỹ thuật chi tiết của tập dữ liệu

| Thuộc tính dữ liệu | Chi tiết thông số cấu trúc |
| :--- | :--- |
| **Tổng số lượng mẫu** | 70.000 hình ảnh sản phẩm thời trang |
| **Phân chia dữ liệu** | • Tập huấn luyện (Training Set): **85%** (59.500 ảnh)<br>• Tập kiểm định (Validation Set): **15%** (10.500 ảnh) |
| **Số lượng nhãn phân loại**| 10 danh mục (Áo thun, Quần dài, Áo len, Váy, Áo khoác, Xăng-đan, Áo sơ mi, Giày thể thao, Túi xách, Giày cổ thấp) |
| **Định dạng cấu trúc ảnh** | Ảnh xám (Grayscale), kích thước chuẩn **28x28 pixel** |

---

## 5. Evaluation Metrics

Mô hình được đánh giá nghiêm ngặt dựa trên hai nhóm chỉ số chính xuyên suốt các kỷ nguyên huấn luyện (Epochs):
* **Độ chính xác (Accuracy):** Đo lường tỷ lệ các mẫu ảnh sản phẩm được phân loại đúng trên tổng số mẫu. Nghiên cứu theo dõi cả Độ chính xác huấn luyện (Training Accuracy) và Độ chính xác kiểm định (Validation Accuracy) để đánh giá khả năng tổng quát hóa.
* **Hàm mất mát (Loss Value):** Sử dụng hàm mất mát để đánh giá độ sai lệch giữa phân phối xác suất dự đoán của mô hình và nhãn thực tế. Giá trị Loss giảm dần và tiệm cận về 0 minh chứng cho khả năng tối ưu hóa tốt của mạng.

---

## 6. Experimental Results

Thực nghiệm cho thấy phương pháp Học chuyển giao đem lại kết quả vượt trội hoàn toàn so với việc thiết kế một mạng CNN thông thường.

### Các kết luận thực nghiệm chính:
* Cả hai mô hình **VGG-19** và **Inception V3** đều đạt tốc độ hội tụ nhanh hơn, đường cong độ chính xác trên tập Validation tăng ổn định và không xảy ra hiện tượng Overfitting nghiêm trọng.
* Nhờ có các bộ lọc đặc trưng mạnh mẽ được tối ưu từ trước, mô hình phân biệt rất nhạy bén các sản phẩm có kiểu dáng gần giống nhau (ví dụ: phân biệt giữa Áo thun, Áo sơ mi và Áo khoác).

### So sánh xu hướng hiệu năng thực nghiệm giữa các mô hình

| Tên mô hình thử nghiệm | Tốc độ hội tụ (Convergence Speed) | Hiệu suất kiểm định (Validation Performance) | Khả năng kiểm soát sai số |
| :--- | :--- | :--- | :--- |
| **CNN tự xây dựng (Baseline)**| Chậm, đồ thị biến động mạnh | Thấp, dễ rơi vào trạng thái bão hòa | Kém, rủi ro Overfitting cao khi tăng số Epoch |
| **VGG-19 (Transfer Learning)** | Nhanh, đường cong mượt mà | Cao, nhận diện tốt các khối cấu trúc phẳng | Tốt, sai số giảm ổn định qua các vòng lặp |
| **Inception V3 (Transfer Learning)**| Rất nhanh nhờ tối ưu số tham số | Rất cao, phân tách chi tiết tốt nhờ các bộ lọc song song | Xuất sắc, hàm mất mát tiệm cận tối tiểu nhanh chóng |

---

## 7. Limitations & Research Gaps

Mặc dù đạt hiệu suất ấn tượng, bài báo vẫn tồn tại một số điểm hạn chế so với môi trường triển khai thực tế:
* **Hạn chế về độ phân giải dữ liệu:** Tập dữ liệu Fashion MNIST chỉ sử dụng ảnh xám 28x28 pixel. Trong thực tế, hình ảnh sản phẩm thương mại điện tử luôn là ảnh màu hệ RGB có độ phân giải cao, độ phức tạp bối cảnh và độ nhiễu lớn hơn rất nhiều.
* **Chi phí tài nguyên khi suy luận (Inference):** Các kiến trúc như VGG-19 hay Inception V3 có dung lượng file mô hình lớn và chứa hàng chục triệu tham số, gây khó khăn lớn nếu muốn tích hợp trực tiếp chạy thời gian thực trên các thiết bị di động hoặc máy chủ tài nguyên hạn chế.
* **Phạm vi kiểm thử hẹp:** Nghiên cứu mới dừng lại ở phân loại ngành hàng thời trang, chưa được kiểm chứng trên các nhóm sản phẩm có hình hình học phi cấu trúc hoặc đa dạng hình thái.

---

## 8. Relevance to Our Topic

Nghiên cứu này cung cấp nền tảng lý thuyết và kỹ thuật thực tiễn quan trọng phục vụ trực tiếp cho việc phát triển và hoàn thiện các module tính năng trong hệ thống phần mềm của nhóm:
* **Tự động hóa quản lý kho và danh mục hàng hóa:** Giải pháp phân loại ảnh này có thể ứng dụng để xây dựng module AI tự động phân nhóm sản phẩm khi người quản trị tải ảnh lên hệ thống. Áp dụng cụ thể vào quy trình vận hành của các cửa hàng bán lẻ đặc sản địa phương (chẳng hạn như các loại mứt, trà, cà phê tại cơ sở DAC SAN ở Đà Lạt), giúp hệ thống tự động nhận diện danh mục và đồng bộ dữ liệu vào cơ sở dữ liệu SQL một cách chính xác mà không cần nhập liệu thủ công.
* **Chuẩn hóa dữ liệu hình ảnh đầu vào:** Phương pháp trích xuất đặc trưng giúp nhóm nhận diện được cấu trúc lõi của sản phẩm, làm cơ sở để tích hợp các thuật toán xử lý ảnh nâng cao. Từ đó, hỗ trợ hệ thống tự động lọc, làm nét hoặc tăng cường chất lượng hình ảnh đối với các bức ảnh chụp sản phẩm từ điện thoại có độ phân giải thấp, giúp cải thiện giao diện hiển thị trên các ứng dụng quản lý hoặc đặt hàng trực tuyến.

---

## 9. Possible Improvements & Future Extensions

Để khắc phục các hạn chế của bài báo và tối ưu hóa mô hình cho hệ thống thực tế của nhóm, các hướng cải tiến sau được đề xuất:

### Kế hoạch cải tiến và mở rộng giải pháp của nhóm

| Khoảng trống của bài báo | Giải pháp cải tiến cụ thể của nhóm | Kỹ thuật triển khai dự kiến |
| :--- | :--- | :--- |
| **Dữ liệu ảnh xám 28x28, không thực tế** | Xây dựng và tự gán nhãn tập dữ liệu ảnh màu (RGB) độ phân giải cao, tập trung vào các mặt hàng thực tế của cửa hàng. | Thu thập ảnh thực tế, sử dụng kỹ thuật Tăng cường dữ liệu (Data Augmentation) như xoay, lật, chỉnh độ sáng. |
| **Ảnh đầu vào dễ bị mờ, thiếu sáng** | Tích hợp tiền xử lý ảnh thông minh trước khi đưa vào mô hình phân loại để tăng độ chính xác. | Áp dụng thuật toán **Làm nét ảnh (Sharpening)** và cân bằng độ tương phản tự động bằng AI. |
| **Mô hình quá nặng, tốn tài nguyên**| Thay thế VGG-19/Inception V3 bằng các kiến trúc mạng gọn nhẹ, tối ưu cho thiết bị phần cứng thông thường. | Thử nghiệm áp dụng các mô hình cải tiến như **MobileNetV3** hoặc **EfficientNet** để giảm kích thước file và tăng tốc độ suy luận. |
| **Đầu ra chỉ dừng lại ở việc gán nhãn**| Phát triển tính năng xử lý hậu kỳ (Post-processing) phục vụ công tác truyền thông và hiển thị sản phẩm. | Ứng dụng AI tự động tách nền sản phẩm (Background Removal) và **ghép sản phẩm vào các khung cảnh sinh động** (ví dụ: bối cảnh đặc trưng của Đà Lạt) để làm tư liệu marketing trực tiếp trên hệ thống. |
| **Chưa tích hợp vào hệ thống phần mềm**| Đóng gói mô hình thành một dịch vụ độc lập kết nối trực tiếp với hệ thống quản lý tổng thể. | Triển khai mô hình dưới dạng một Web Service (Flask/FastAPI hoặc module Java AI), kết nối trực tiếp với backend Java và cơ sở dữ liệu SQL của nhóm để tự động cập nhật trạng thái đơn hàng và phân loại hàng hóa. |
