# Topic Proposal

## 1. Group Information
- **Class**: SE2037
- **Group**: Group2
- **Leader**: Nguyen Duy Hoang
- **Members**:
	- Bui Van Nghia
 	- Nguyen Thanh Son
	- Nhieu Si Luan
 	- Nguyen Dinh Nhat Dinh
 	- Dao Trong Tan

## 2. Proposed Title
- **English title:** Automated E-commerce Product Categorization System from Images using Convolutional Neural Networks (CNN).
- **Vietnamese title:** Hệ thống tự động phân loại danh mục sản phẩm thương mại điện tử qua hình ảnh sử dụng Mạng nơ-ron tích chập (CNN).

## 3. Application Domain
- E-commerce (Thương mại điện tử).
- Computer Vision (Thị giác máy tính).

## 4. Problem Statement
Trên các nền tảng thương mại điện tử, việc phân loại sản phẩm vào đúng danh mục (ví dụ: Quần áo, Đồ điện tử, Gia dụng) là bước bắt buộc để hệ thống tìm kiếm và gợi ý hoạt động hiệu quả. Tuy nhiên, các nhà bán hàng thường phải đối mặt với việc đăng tải hàng trăm, hàng ngàn sản phẩm mỗi ngày. Việc lựa chọn danh mục thủ công không chỉ tiêu tốn nhiều thời gian mà còn dễ dẫn đến sai sót do phân loại nhầm, làm giảm khả năng tiếp cận khách hàng và ảnh hưởng trực tiếp đến doanh thu.

## 5. Motivation
Tự động hóa quy trình phân loại sản phẩm ngay từ bước tải ảnh lên (Upload) sẽ giải quyết triệt để vấn đề trên. Việc áp dụng mô hình Học sâu (Deep Learning) để nhận diện các đặc trưng hình ảnh của sản phẩm sẽ giúp rút ngắn thời gian thao tác cho người bán hàng, đồng thời đảm bảo tính nhất quán và chuẩn xác cho cơ sở dữ liệu của toàn bộ nền tảng thương mại điện tử.

## 6. Target Users
- Chủ shop, người bán hàng trên các nền tảng thương mại điện tử (Sellers/Merchants).
- Quản trị viên nền tảng E-commerce (Platform Administrators).
- Nhân viên quản lý danh mục sản phẩm (Catalog Managers).

## 7. Proposed AI Model / Method
- **Phương pháp cốt lõi:** Thị giác máy tính (Computer Vision) kết hợp Học sâu (Deep Learning).
- **Mô hình kiến trúc:** Mạng nơ-ron tích chập (Convolutional Neural Networks - CNN). Dự án sẽ áp dụng kỹ thuật Transfer Learning với các kiến trúc đã được tối ưu hóa như ResNet hoặc MobileNet để trích xuất đặc trưng hình ảnh với độ chính xác cao mà không đòi hỏi tài nguyên huấn luyện khổng lồ.

## 8. System Features
- **Giao diện quản lý (Merchant Dashboard):** Cho phép người bán hàng tải lên hình ảnh sản phẩm mới cần đăng bán.
- **Tiền xử lý ảnh tự động:** Hệ thống tự động thay đổi kích thước (resize) và chuẩn hóa (normalize) hình ảnh để phù hợp với định dạng đầu vào của mô hình AI.
- **Phân loại AI tự động (Auto-Tagging):** Phân tích hình ảnh và trả về top 3 danh mục có khả năng khớp nhất kèm theo tỷ lệ tự tin (Confidence Score).
- **Backend & AI Service:** Hệ thống được thiết kế nguyên khối để tối ưu việc triển khai prototype. Nền tảng Java đóng vai trò xử lý logic nghiệp vụ và quản lý cơ sở dữ liệu, đồng thời tích hợp trực tiếp với một module Python làm bộ máy suy luận AI nội bộ. Cách tiếp cận này loại bỏ sự phức tạp của kiến trúc phân tán (microservices), giúp dự án dễ bảo trì mà vẫn tận dụng được thế mạnh quản lý phần mềm của Java và hệ sinh thái AI của Python.

## 9. Expected Contribution
- Xây dựng thành công quy trình tự động hóa (Data Pipeline) kết nối giữa giao diện người dùng, hệ thống quản lý Backend và dịch vụ suy luận AI.
- Đánh giá và so sánh hiệu năng của các mô hình CNN khác nhau trên bộ dữ liệu hình ảnh sản phẩm thương mại điện tử thực tế.
- Cung cấp một Prototype phần mềm có tính ứng dụng cao, giải quyết trực tiếp bài toán vận hành của các sàn giao dịch trực tuyến.

## 10. Evaluation Plan
- **Dataset:** Sử dụng các bộ dữ liệu ảnh sản phẩm mã nguồn mở trên Kaggle (ví dụ: Fashion Product Images Dataset hoặc E-Commerce Products Image Dataset).
- **Baseline:** Đánh giá hiệu năng AI bằng cách so sánh với các thuật toán Học máy truyền thống chuyên về phân loại hình ảnh (như SVM kết hợp trích xuất đặc trưng HOG). Đánh giá hiệu năng hệ thống bằng cách đo lường thời gian thao tác upload một sản phẩm có AI hỗ trợ so với thao tác chọn tay thủ công.
- **Metrics:**
  - Accuracy (Độ chính xác tổng thể).
  - Precision, Recall, và F1-Score cho từng danh mục sản phẩm nhằm đánh giá mức độ nhận diện đồng đều.
- **Expert evaluation:** Không áp dụng.
- **User survey:** Không áp dụng.

## 11. Related Papers
| No | Title | Year | Source | Link / DOI |
| :--- | :--- | :--- | :--- | :--- |
| 1 | E-Commerce Product Image Classification using Transfer Learning | 2021 | IEEE | [10.1109/ICCMC51019.2021.9418371](https://ieeexplore.ieee.org/document/9418371) |
| 2 | Research on Classification of Cross-Border E-Commerce Products Based on Image Recognition and Deep Learning | 2021 | IEEE Access | [10.1109/ACCESS.2020.3020737](https://ieeexplore.ieee.org/document/9181535) |
| 3 | A Scalable Framework for Product Image Classification applied to Home Improvement E-commerce | 2021 | ACM (DLP-KDD) | [DLP-KDD 2021 Paper 14](https://dlp-kdd.github.io/assets/pdf/DLP-KDD_2021_paper_14.pdf) |
| 4 | Hybrid Deep Learning Approach for Product Categorization in E-commerce | 2024 | AIP Publishing | [10.1063/5.0198666](https://pubs.aip.org/aip/acp/article-abstract/3072/1/040018/3277811/Hybrid-deep-learning-approach-for-product?redirectedFrom=fulltext) |
| 5 | Fine-Grained Classification of Product Images Based on Convolutional Neural Networks | 2018 | SCIRP | [10.4236/jcc.2018.61001](https://www.scirp.org/journal/paperinformation?paperid=88032) |
