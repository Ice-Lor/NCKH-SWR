# Paper 01 Summary

## Citation

- **Tên bài báo:** KAQG: A Knowledge-Graph-Enhanced RAG for Difficulty-Controlled Question Generation
- **Tác giả:** Ching Han Chen, Ming Fang Shiu
- **Năm:** 2025
- **Nguồn:** arXiv / IEEE TechRxiv
- **Link / DOI:** https://arxiv.org/abs/2505.07618

## Problem

Nghiên cứu giải quyết vấn đề kiểm soát độ khó câu hỏi kiểm tra, hiệu chuẩn tâm lý học đo lường (psychometric calibration) và căn chỉnh nhận thức (cognitive alignment) trong các hệ thống tự động tạo câu hỏi trắc nghiệm (AQG). Mặc dù các mô hình ngôn ngữ lớn (LLMs) và các framework RAG thông thường (như GraphRAG, HippoRAG, LightRAG) cải thiện tính chính xác của thông tin, chúng thiếu cơ chế kiểm soát có hệ thống về độ khó nhận thức (như theo Bloom's Taxonomy) và tính hiệu lực đo lường (như theo Item Response Theory - IRT), điều vốn vô cùng quan trọng đối với các kỳ thi đánh giá năng lực chuẩn hóa.

## Method

Framework đề xuất có tên là **KAQG (Knowledge Augmented Question Generation)**, tích hợp Item Response Theory (IRT), Bloom’s Taxonomy và Đồ thị tri thức (Knowledge Graphs - KG) vào một hệ thống RAG đa tác vụ (multi-agent) phân tán. Các đặc điểm chính gồm:
1. **Kiến trúc Cách ly Đa Đồ thị (Multi-Graph Isolation):** Mỗi chủ đề môn học được hỗ trợ bởi một đồ thị tri thức độc lập nhằm loại bỏ hiện tượng nhiễu thuật ngữ liên miền.
2. **PageRank-based Concept Weighting:** Xếp hạng và lựa chọn các khái niệm học tập cốt lõi trong KG bằng thuật toán PageRank để đảm bảo câu hỏi bao phủ đúng trọng tâm chương trình giảng dạy.
3. **Hiệu chuẩn tham số IRT 3PL:** Ánh xạ các thuộc tính đồ thị và nhận thức vào mô hình IRT 3 tham số:
   - Tham số khó ($b$): Tương thích với độ sâu đồ thị và các bậc nhận thức Bloom cao (như Analyze, Evaluate).
   - Tham số phân hóa ($a$): Tương thích với độ kết nối của nút khái niệm trong đồ thị.
   - Tham số đoán mò ($c$): Giảm thiểu thông qua suy luận đa bước (multi-hop reasoning) trên đồ thị tri thức để sinh distractors có độ nhiễu hợp lý.
4. **Đánh giá đặc trưng bề mặt câu hỏi:** Đánh giá độ khó dựa trên tổ hợp 7 đặc trưng của câu hỏi trắc nghiệm (stem length, domain vocabulary, cognitive demand, option length, option similarity, stem-option overlap, distractor plausibility) để tính điểm độ khó tổng quát.
5. **Kiến trúc Multi-Agent phân tán:** Điều phối các Agent chuyên biệt (Retriever, Generator, Evaluator) qua Data Distribution Service (DDS) theo mô hình publish-subscribe để tăng hiệu năng và tính chống chịu lỗi.

## Dataset

- Hệ thống sử dụng cơ sở tri thức xây dựng từ **102 PDF giáo trình chuyên ngành** và tài liệu giảng dạy.
- Để đánh giá so sánh, nhóm nghiên cứu sử dụng **3 bài đọc thuộc kỳ thi chuẩn hóa ACT Reading** (Passage A, B, C) kèm 10 câu hỏi chính thức cho mỗi bài làm nhóm đối chứng (Control).

## Evaluation

Nghiên cứu sử dụng hai quy trình đánh giá bổ trợ:
1. **Human Benchmarking (Đánh giá thực nghiệm với con người):** Tuyển dụng người tham gia chia thành 4 nhóm để thực hiện bài thi gồm: Nhóm câu hỏi ACT chính thức (đối chứng) và 3 nhóm câu hỏi do hệ thống sinh ra ở các mức độ khó Low, Medium, High. Các chỉ số đo lường gồm tỷ lệ làm đúng (P-value / Difficulty), chỉ số phân hóa (Discrimination Index) và điểm đánh giá của chuyên gia (Expert Rating) về chất lượng câu hỏi (thang Likert 5 điểm).
2. **Simulation Study (Nghiên cứu mô phỏng máy tính):** Mô phỏng 5,000 thí sinh ảo với phân phối năng lực $\theta_i \sim N(0,1)$. Sử dụng mô hình 3PL để sinh ma trận trả lời cho 90 câu hỏi (chia đều 3 mức độ khó). Áp dụng ước lượng IRT để so sánh tham số khôi phục được với tham số gốc thực tế. Đồng thời thực hiện thử nghiệm cắt bỏ (ablation study) trên 5 điều kiện khác nhau (Full, -IRT, -Bloom, -IRT&Bloom, Baseline-RAG).

## Results

1. **Thực nghiệm với con người:** Hệ thống điều khiển độ khó rất ổn định. Nhóm Low có tỷ lệ đúng trung bình cao nhất ($P = 0.82 \pm 0.06$), nhóm Medium ($P = 0.71 \pm 0.07$) tương đồng với đề ACT chính thức ($P = 0.76 \pm 0.05$), và nhóm High có độ khó cao nhất ($P = 0.63 \pm 0.08$). Chỉ số phân hóa được duy trì ổn định ở các nhóm ($0.32 - 0.37$), chứng tỏ hệ thống thay đổi độ khó mà không làm giảm khả năng phân loại năng lực thí sinh.
2. **Nghiên cứu mô phỏng:** Mô hình Full khôi phục tham số đạt tương quan rất cao với ground-truth đối với difficulty $b$ (hệ số tương quan $0.91$, sai số RMSE $0.22$) và discrimination $a$ ($0.82$). Tỷ lệ phân loại sai mức độ khó chỉ là $6.7\%$, vượt trội rõ rệt so với các điều kiện thiếu hụt IRT/Bloom (tỷ lệ sai từ $12.5\%$ đến $27.8\%$).

## Limitations

- **Kiến trúc phức tạp:** Việc thiết lập đồ thị tri thức, hệ thống multi-agent kết hợp giao thức truyền thông DDS đòi hỏi tài nguyên tính toán lớn và kỹ thuật phức tạp, khó tích hợp trực tiếp vào các hệ thống LMS gọn nhẹ.
- **Dựa vào chuyên gia ban đầu:** Trọng số của 7 đặc trưng độ khó ban đầu vẫn phụ thuộc vào đánh giá chủ quan của chuyên gia, chưa được tối ưu hoàn toàn bằng dữ liệu thực nghiệm quy mô lớn từ người dùng thật.
- **Nhiễu trích xuất đầu vào:** Việc trích xuất thực thể và quan hệ từ các tài liệu PDF quét (scanned) bị mờ hoặc chứa nhiều thuật ngữ viết tắt dễ bị sai sót, cần thêm cơ chế hậu xử lý chuẩn hóa thực thể.

## Relevance to our topic

- Khẳng định tính khả thi của việc tích hợp lý thuyết giáo dục (Bloom's Taxonomy) và đo lường học thuật (IRT) vào prompt để kiểm soát độ khó câu hỏi được sinh ra bám sát chuẩn đầu ra (CLO) của môn học.
- Đồ thị tri thức và thuật toán PageRank cung cấp giải pháp lọc và lựa chọn các khái niệm cốt lõi trong slide bài giảng để tập trung sinh câu hỏi trọng tâm, tránh việc sinh câu hỏi lan man.

## Possible improvement

- **Đơn giản hóa hệ thống:** Lược bỏ cơ chế DDS phức tạp, thay thế bằng luồng RAG tuần tự tích hợp trực tiếp trong API của LMS để tối ưu tốc độ phản hồi.
- **Bổ sung giải thích đáp án sai:** Bổ sung module sinh phản hồi giải thích chi tiết cho từng lựa chọn sai (distractors feedback) dựa trên các mối liên kết ngữ nghĩa trong đồ thị tri thức, hỗ trợ việc tự học của sinh viên tốt hơn.
