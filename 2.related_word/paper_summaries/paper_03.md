# Paper 03 Summary: Fine-Grained Classification of Product Images Based on Convolutional Neural Networks

## 1. Citation

* **Tên bài báo:** Fine-Grained Classification of Product Images Based on Convolutional Neural Networks
* **Tác giả:** Tongtong Liu, Rubing Wang, Jikang Chen, Shengliang Han, Jimin Yang
* **Năm xuất bản:** 2018
* **Nguồn phát hành:** Advances in Molecular Imaging, Vol.8 No.4
* **DOI / Link:** [10.4236/ami.2018.84007](https://doi.org/10.4236/ami.2018.84007)

---

## 2. Problem Statement

Bài báo tập trung giải quyết các thách thức trong việc phân loại hình ảnh sản phẩm thương mại điện tử:
* **Hạn chế của phương pháp truyền thống:** Các phương pháp dựa trên từ khóa, nhãn dán hoặc thuộc tính ngữ nghĩa không thể hiện được đầy đủ các đặc điểm phong phú của hình ảnh sản phẩm. Việc sử dụng các đặc trưng nội dung như hình dạng, màu sắc hay kết cấu rất khó để áp dụng phổ quát cho toàn bộ các loại danh mục hàng hóa.
* **Nhược điểm của mạng CNN sâu:** Quá trình huấn luyện mạng nơ-ron tích chập sâu thường tiêu tốn quá nhiều thời gian và chiếm dụng một lượng lớn tài nguyên phần cứng.
* **Mục tiêu cốt lõi:** Đề xuất và huấn luyện các mô hình mạng nơ-ron tích chập (bao gồm cả mạng sâu và mạng nông) nhằm đạt được độ chính xác phân loại cao, đồng thời giải quyết bài toán tiêu tốn tài nguyên và thời gian huấn luyện của các mạng học sâu.

---

## 3. Proposed Method

Nghiên cứu đề xuất xây dựng cấu trúc mạng CNN mới được thiết kế đặc thù cho bài toán phân loại sản phẩm với 3 giai đoạn chính:
1.  **Tiền xử lý và Tăng cường dữ liệu (Data Augmentation):** Sử dụng các phép biến đổi affine như lật ngang, lật dọc và xoay ảnh (các góc 90 độ và 180 độ) để nhân bản dữ liệu lên gấp 5 lần, giúp mô hình có khả năng tổng quát hóa tốt hơn với lượng dữ liệu đầu vào hạn chế.
2.  **Trích xuất đặc trưng (Feature Extraction):** Thiết kế mạng CNN với các lớp tích chập (Convolutional Layers) và lớp gộp (Max-pooling Layers) để tự động trích xuất các đặc trưng. Cụ thể, mạng sâu gồm một lớp tích chập 7x7, một lớp gộp 3x3, một lớp tích chập 5x5, một lớp gộp 2x2 và ba lớp tích chập 3x3. Kỹ thuật Dropout 50% được áp dụng trước các lớp kết nối đầy đủ (Fully Connected) để ngăn chặn hiện tượng học vẹt (Overfitting).
3.  **Phân loại (Softmax Classification):** Sử dụng lớp phân loại Softmax ở cuối để phân loại ảnh đầu vào thành 20 danh mục sản phẩm khác nhau. Bên cạnh cấu trúc mạng CNN sâu, một kiến trúc mạng CNN nông (Shallow CNN) cũng được thiết kế nhằm đạt độ chính xác tương đương nhưng tối ưu hơn về thời gian huấn luyện.

---

## 4. Dataset Characteristics

Nghiên cứu sử dụng hai tập dữ liệu chính để huấn luyện và kiểm thử mạng CNN:

### Thông số kỹ thuật chi tiết của các tập dữ liệu

| Tập dữ liệu | Chi tiết thông số cấu trúc |
| :--- | :--- |
| **Caltech256 Database** | • Chọn lọc 20 danh mục đối tượng có tính tương đồng với hình ảnh sản phẩm.<br>• Phân chia: Chọn ngẫu nhiên 100 ảnh để huấn luyện và 50 ảnh để kiểm thử cho mỗi danh mục. |
| **Homemade Database** | • Thu thập trực tiếp từ các trang thương mại điện tử: T-mall, Jingdong và Amazon.<br>• Gồm 20 loại sản phẩm (15 loại quần áo và 5 loại giày dép), mỗi loại khởi điểm có 200 ảnh.<br>• Phân chia sau khi tăng cường dữ liệu (tổng 20.000 ảnh): **16.000 ảnh** cho tập Training và **4.000 ảnh** cho tập Testing. |
| **Định dạng cấu trúc ảnh**| Cả hai tập dữ liệu đều được chuẩn hóa về định dạng ảnh màu RGB với kích thước cố định là **256x256 pixels**. |

---

## 5. Evaluation Metrics

Hiệu năng của mô hình được đánh giá chủ yếu thông qua chỉ số:
* **Độ chính xác phân loại (Classification Accuracy):** Đánh giá và đo lường hiệu suất phân loại của mạng nơ-ron trên các cơ sở dữ liệu bằng cách tính tỷ lệ ảnh được dự đoán đúng danh mục.

---

## 6. Experimental Results

Thực nghiệm đã chứng minh tính hiệu quả vượt trội của mạng CNN đề xuất so với các phương pháp trước đó:

### Các kết luận thực nghiệm chính:
* **Mô hình học máy truyền thống:** Việc kết hợp kỹ thuật trích xuất đặc trưng nội dung với máy học truyền thống SVM chỉ đem lại độ chính xác dao động từ 76.3% đến 86.2%.
* **Mạng CNN sâu (Deep CNN):** Kiến trúc sâu đề xuất đã đạt được mức độ chính xác phân loại ấn tượng lên tới **92.1%**.
* **Mạng CNN nông (Shallow CNN):** Kiến trúc mạng nông cũng đạt được độ chính xác rất cao là **90.6%**, hoàn thành tốt mục tiêu duy trì hiệu năng trong khi giải quyết triệt để bài toán về tiêu tốn tài nguyên và thời gian huấn luyện.

---

## 7. Limitations & Research Gaps

Dựa trên phương pháp tiếp cận thực tế của bài báo, có thể nhận thấy một số điểm hạn chế:
* **Môi trường dữ liệu có kiểm soát:** Hình ảnh đầu vào được yêu cầu chuẩn hóa chặt chẽ về kích thước cố định (256x256 pixel). Trong môi trường thực tế, dữ liệu ảnh sản phẩm do người dùng tải lên rất đa dạng về tỷ lệ khung hình và độ phân giải.
* **Quy mô danh mục thử nghiệm hẹp:** Tập dữ liệu tự xây dựng mới giới hạn ở phạm vi 20 danh mục thuộc nhóm ngành quần áo và giày dép. Mức độ này chưa bao phủ được sự phức tạp và đa dạng hình thái của hàng ngàn ngành hàng trên các nền tảng quản lý hiện nay.

---

## 8. Relevance to Our Topic

Nghiên cứu này cung cấp cơ sở kỹ thuật quan trọng để hoàn thiện dự án Lab lớn của bộ môn Cơ sở dữ liệu mà nhóm 5 thành viên đang thực hiện. Việc ứng dụng mạng CNN để tự động nhận diện và phân loại sản phẩm hỗ trợ đắc lực cho quy trình thiết kế cơ sở dữ liệu thực tế:
* **Tự động hóa luồng dữ liệu:** Thay vì các thành viên trong nhóm phải tạo các module nhập liệu thủ công rườm rà, giải pháp phân loại ảnh này có thể hoạt động như một dịch vụ nền. Khi hình ảnh được tải lên, mạng CNN lập tức dự đoán danh mục và trả kết quả để hệ thống ghi trực tiếp vào các bảng dữ liệu tương ứng.
* **Tối ưu hóa kiến trúc hệ thống:** Việc bài báo đề xuất thành công kiến trúc mạng "CNN nông" (Shallow CNN) với độ chính xác lên tới 90.6% mở ra hướng đi rất phù hợp. Nhóm có thể tích hợp một mô hình AI có cấu trúc gọn nhẹ, ít tiêu tốn tài nguyên, đảm bảo tốc độ phản hồi nhanh chóng khi truy vấn và cập nhật cơ sở dữ liệu liên tục.

---

## 9. Possible Improvements & Future Extensions

Để tối ưu hóa mô hình từ bài báo cho hệ thống của nhóm, các hướng cải tiến sau được đề xuất:

### Kế hoạch cải tiến và mở rộng giải pháp của nhóm

| Khoảng trống của bài báo | Giải pháp cải tiến cụ thể của nhóm | Kỹ thuật triển khai dự kiến |
| :--- | :--- | :--- |
| **Dữ liệu chuẩn hóa tĩnh (256x256)** | Xây dựng pipeline xử lý ảnh động linh hoạt, cho phép tiếp nhận mọi kích thước và định dạng ảnh đầu vào từ người dùng hoặc quản trị viên. | Sử dụng thư viện xử lý ảnh tự động cắt xén trọng tâm (Center Crop), thu phóng và thêm viền (Padding) để chuẩn hóa kích thước trước khi đẩy vào mô hình AI. |
| **Giới hạn thử nghiệm 20 danh mục** | Mở rộng quy mô phân loại để bao phủ nhiều danh mục hàng hóa khác nhau, đảm bảo bám sát với bản thiết kế các bảng thực thể (Entity) trong hệ thống cơ sở dữ liệu. | Thu thập thêm dữ liệu hình ảnh đa dạng và thực hiện quy trình huấn luyện tinh chỉnh (Fine-tuning) để mô hình nhận diện thêm các nhãn hàng hóa mới. |
| **Chưa có cơ chế xử lý ngoại lệ** | Phát triển kịch bản dự phòng bảo vệ tính toàn vẹn dữ liệu khi mô hình dự đoán sai hoặc độ tự tin (Confidence score) quá thấp. | Tích hợp logic ràng buộc: Nếu độ tự tin của hàm Softmax < 80%, hệ thống sẽ tự động chuyển ảnh vào hàng đợi (Queue) để một thành viên trong nhóm duyệt thủ công trước khi thực thi lệnh `INSERT` vào database. |