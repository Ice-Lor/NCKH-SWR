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

- **English title**: Applying Artificial Intelligence to Customer Service Management Systems
- **Vietnamese title**: Áp dụng AI vào hệ thống quản lí dịch vụ chăm sóc khách hàng

## 3. Application Domain

Customer Care Services (Dịch vụ Chăm sóc Khách hàng)

## 4. Problem Statement

Trong thời đại số hóa, các doanh nghiệp phải tiếp nhận hàng trăm, hàng ngàn lượt yêu cầu hỗ trợ từ khách hàng mỗi ngày qua nhiều kênh khác nhau. Việc vận hành một đội ngũ nhân viên chăm sóc khách hàng (CSKH) truyền thống gặp phải nhiều thách thức lớn:

- **Thời gian phản hồi chậm**: Khách hàng phải chờ đợi lâu, đặc biệt là ngoài giờ làm việc hoặc trong các khung giờ cao điểm.
- **Chi phí vận hành cao**: Doanh nghiệp tốn nhiều chi phí cho việc tuyển dụng, đào tạo và duy trì nhân sự trực tổng đài xoay ca liên tục.
- **Thiếu tính cá nhân hóa**: Nhân viên khó có thể bao quát và ghi nhớ hết lịch sử, thói quen cũng như sở thích của từng khách hàng để đưa ra những tư vấn chính xác, kịp thời.
- **Bỏ sót dữ liệu**: Dữ liệu thu thập từ các cuộc hội thoại, phản hồi chưa được khai thác hiệu quả để tối ưu hóa quy trình kinh doanh và nâng cấp chất lượng sản phẩm.

## 5. Motivation

Việc tích hợp trí tuệ nhân tạo (AI) vào hệ thống quản lý CSKH không chỉ giúp doanh nghiệp tối ưu hóa chi phí vận hành mà còn nâng cao trải nghiệm người dùng một cách vượt trội. 

Hệ thống có khả năng hoạt động liên tục 24/7, phản hồi ngay lập tức với độ chính xác cao nhờ vào việc khai thác kho kiến thức nội bộ của doanh nghiệp. Ngoài ra, việc AI phân tích sâu dữ liệu tương tác sẽ giúp doanh nghiệp đưa ra các chiến lược kinh doanh phù hợp, thấu hiểu khách hàng tốt hơn và tối ưu hóa tỷ lệ giữ chân khách hàng (customer retention) hiệu quả.

## 6. Target Users

- **Khách hàng của doanh nghiệp**: Người cần được giải đáp thắc mắc, hỗ trợ kỹ thuật hoặc tư vấn mua hàng một cách nhanh chóng và chính xác.
- **Nhân viên CSKH / Tư vấn viên**: Sử dụng AI như một trợ lý đắc lực để soạn thảo câu trả lời nhanh, tra cứu thông tin sản phẩm và quản lý thông tin khách hàng một cách tối ưu.
- **Quản lý / Chủ doanh nghiệp**: Theo dõi báo cáo trực quan, đánh giá hiệu suất của đội ngũ CSKH và xem các phân tích xu hướng tiêu dùng, tâm lý khách hàng từ mô hình AI.

## 7. Proposed AI Model / Method

Hệ thống dự kiến kết hợp các mô hình và phương pháp AI tiên tiến sau:

- **LLM (Large Language Model - ví dụ: GPT-4o, Claude 3.5 Sonnet hoặc Llama 3)**: Đóng vai trò cốt lõi trong việc hiểu ngữ nghĩa câu hỏi phức tạp và sinh câu trả lời tự nhiên, mạch lạc như người thật.
- **RAG (Retrieval-Augmented Generation)**: Kết nối LLM với cơ sở dữ liệu nội bộ của doanh nghiệp (thông tin sản phẩm, chính sách bảo hành, FAQs) nhằm đảm bảo AI trả lời chính xác dữ liệu thực tế, giảm thiểu tối đa hiện tượng "ảo tưởng" (hallucination).
- **Embedding model (ví dụ: text-embedding-3-small)**: Chuyển đổi dữ liệu văn bản thành các vector không gian để phục vụ cho việc tìm kiếm ngữ nghĩa chính xác trong quy trình RAG.
- **Sentiment Analysis (Phân tích cảm xúc)**: Sử dụng các mô hình phân loại (như BERT hoặc RoBERTa tinh chỉnh) để nhận diện tâm trạng khách hàng theo thời gian thực (tức giận, hài lòng, trung lập), từ đó đưa ra cảnh báo hoặc chuyển hướng cuộc gọi đến nhân viên kịp thời.

## 8. System Features

Các chức năng chính của hệ thống bao gồm:

1. **Quản lý thông tin khách hàng thông minh (Smart CRM Dashboard)**: Lưu trữ hồ sơ lịch sử mua hàng và tự động tóm tắt (summarize) nội dung các lần tương tác trước đó của khách hàng bằng AI.
2. **Trợ lý Chatbot AI 24/7 (RAG-based Chatbot)**: Tự động tiếp nhận và trả lời các câu hỏi về sản phẩm, dịch vụ, chính sách dựa trên tài liệu chuẩn do doanh nghiệp cung cấp.
3. **Hệ thống phân tích cảm xúc & Gợi ý phản hồi (Sentiment Analysis & Smart Reply)**: Phân tích thái độ của khách hàng theo thời gian thực trong phòng chat và tự động gợi ý câu trả lời tối ưu nhất cho nhân viên CSKH duyệt nhanh.
4. **Phân tích dữ liệu & Dự báo xu hướng (Analytics & Insights)**: Thống kê các nhóm vấn đề khách hàng thường gặp phải, đánh giá biểu đồ mức độ hài lòng và dự báo tỷ lệ rời bỏ dịch vụ (Churn Prediction).

## 9. Expected Contribution

Đóng góp dự kiến của đề tài nghiên cứu:

1. **Xây dựng hệ thống CRM tích hợp AI hoàn chỉnh**: Kết hợp mượt mà giữa quản lý dữ liệu khách hàng truyền thống và các công nghệ AI tạo sinh (Generative AI) hiện đại vào cùng một nền tảng.
2. **Tối ưu hóa độ chính xác của Chatbot nghiệp vụ**: Áp dụng thành công kỹ thuật RAG giúp chatbot trả lời đúng trọng tâm tài liệu doanh nghiệp, kiểm soát và giảm tỷ lệ sai sót thông tin xuống dưới 5%.
3. **Cải thiện hiệu suất vận hành CSKH**: Giảm tải đến 70% các câu hỏi trùng lặp, cơ bản cho đội ngũ nhân sự, đồng thời rút ngắn thời gian phản hồi trung bình của doanh nghiệp xuống mức tính bằng giây.

## 10. Evaluation Plan

Hệ thống sẽ được đánh giá toàn diện thông qua các phương pháp sau:

- **Dataset**: Sử dụng tập dữ liệu hội thoại CSKH công khai chuẩn hóa (ví dụ: *Customer Support on Twitter dataset*) kết hợp với bộ dữ liệu FAQs tự xây dựng mô phỏng theo nghiệp vụ thực tế của một doanh nghiệp cụ thể.
- **Baseline**: So sánh hiệu quả thực tế với các chatbot dạng kịch bản cứng (Rule-based chatbot) truyền thống hoặc mô hình LLM thuần túy không áp dụng kỹ thuật RAG.
- **Metrics**:
  - *Đánh giá AI*: Sử dụng các chỉ số ROUGE, BLEU score, hoặc khung đánh giá chuyên dụng **RAGAS** (để đo lường chi tiết độ liên quan của ngữ cảnh được truy xuất và tính chính xác của câu trả lời được sinh ra).
  - *Đánh giá hệ thống*: Đo lường thời gian phản hồi (Response Time) và tỷ lệ giải quyết được vấn đề trực tuyến (Resolution Rate).
- **Expert evaluation**: Xin ý kiến đánh giá từ giảng viên hướng dẫn hoặc các chuyên gia có kinh nghiệm lâu năm trong lĩnh vực CRM/AI để tối ưu quy trình nghiệp vụ và giao diện.
- **User survey**: Khảo sát trải nghiệm người dùng thực tế qua biểu mẫu đánh giá điểm số hài lòng cá nhân (CSAT - Customer Satisfaction Score) để kiểm tra độ thân thiện và hữu ích của hệ thống.

## 11. Related Papers

Dưới đây là danh sách các bài báo khoa học liên quan làm nền tảng nghiên cứu cho đề tài:

| No | Title | Year | Source | Link / DOI |
|---|---|---|---|---|
| 1 | Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks | 2020 | NeurIPS | arXiv:2005.11401 |
| 2 | BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding | 2019 | NAACL | arXiv:1810.04805 |
| 3 | A Survey on Large Language Models for Enterprise Applications | 2024 | arXiv | arXiv:2402.00001 |
| 4 | Transformer-based Sentiment Analysis for Customer Service Reviews | 2022 | IEEE Access | 10.1109/ACCESS.2022.314 |
| 5 | Artificial Intelligence in Customer Relationship Management: A Literature Review | 2021 | International Journal of Information Management | 10.1016/j.ijinfomgt.2021.102381 |
