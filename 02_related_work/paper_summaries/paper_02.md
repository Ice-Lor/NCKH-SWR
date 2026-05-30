# Paper 02 Summary

## Citation

- **Tên bài báo:** Leveraging In-Context Learning and Retrieval-Augmented Generation for Automatic Question Generation in Educational Domains
- **Tác giả:** Subhankar Maity, Aniket Deroy, Sudeshna Sarkar
- **Năm:** 2025
- **Nguồn:** arXiv
- **Link / DOI:** https://arxiv.org/abs/2501.17397

## Problem

Nghiên cứu giải quyết bài toán tự động tạo câu hỏi trắc nghiệm/tự luận giáo dục (AQG) có chất lượng sư phạm và phù hợp ngữ cảnh. Các phương pháp tạo câu hỏi truyền thống thường sinh ra câu hỏi xa rời ngữ cảnh bài học hoặc thiếu tính sư phạm. Trong khi đó, các mô hình fine-tuning học sâu (như T5, BART) đòi hỏi lượng dữ liệu gán nhãn chuyên biệt rất lớn, vốn cực kỳ khan hiếm trong lĩnh vực giáo dục. Ngoài ra, LLM thuần túy khi sinh câu hỏi không có ngữ cảnh bổ trợ thường dễ xảy ra hiện tượng ảo giác (hallucination).

## Method

Nghiên cứu tiến hành so sánh toàn diện hai phương pháp tiếp cận hiện đại:
1. **In-Context Learning (ICL):** Sử dụng mô hình GPT-4 với các prompt few-shot ($k$ = 3, 5, 7 ví dụ) để định hướng cấu trúc câu hỏi mà không làm thay đổi trọng số mô hình.
2. **Retrieval-Augmented Generation (RAG):** Sử dụng mô hình BART-large kết hợp với mô-đun truy xuất FAISS để tìm kiếm các tài liệu bổ trợ liên quan nhất từ kho sách giáo khoa NCERT, sau đó ghép nối vào ngữ cảnh để sinh câu hỏi.
3. **Mô hình lai (Hybrid Model - Đề xuất chính):** Kết hợp sức mạnh của cả hai. Đầu tiên, hệ thống dùng FAISS truy xuất top $k=5$ tài liệu liên quan để làm giàu ngữ cảnh đầu vào (như RAG), sau đó chuyển ngữ cảnh kết hợp này cùng với prompt few-shot ($k=5$ ví dụ) vào GPT-4 (như ICL) để tiến hành tạo sinh câu hỏi.

Nhóm nghiên cứu so sánh các mô hình trên với các Baseline đã được fine-tune trực tiếp trên tập dữ liệu đích gồm T5-large và BART-large.

## Dataset

Sử dụng tập dữ liệu **EduProbe** gồm **3,502 cặp câu hỏi-đáp án** được biên soạn từ sách giáo khoa của Hội đồng Nghiên cứu và Đào tạo Giáo dục Quốc gia Ấn Độ (NCERT) cấp lớp từ 6 đến 12. Phân bổ môn học bao gồm:
- Lịch sử (History): 858 cặp.
- Địa lý (Geography): 861 cặp.
- Kinh tế (Economics): 802 cặp.
- Nghiên cứu Môi trường (Environmental Studies): 606 cặp.
- Khoa học (Science): 375 cặp.

## Evaluation

Nghiên cứu kết hợp hai phương thức đánh giá:
1. **Đánh giá tự động (Automated Metrics):** Đo lường chất lượng ngôn ngữ bằng các chỉ số BLEU-4, ROUGE-L, METEOR, ChRF và BERTScore (sử dụng gói SummEval).
2. **Đánh giá con người (Human Evaluation):** Ban giám khảo gồm 3 giáo viên trung học và 2 học sinh tiến hành đánh giá chéo ngẫu nhiên 1,400 câu hỏi tạo ra bởi 7 cấu hình khác nhau. Câu hỏi được chấm điểm trên thang đo Likert từ 1 đến 5 theo 5 tiêu chí sư phạm: Grammaticality (Ngữ pháp), Appropriateness (Sự phù hợp ngữ nghĩa độc lập ngữ cảnh), Relevance (Độ liên quan ngữ cảnh), Complexity (Độ phức tạp nhận thức), và Answerability (Khả năng trả lời được từ ngữ cảnh). Độ đồng thuận của raters được kiểm chứng bằng Fleiss's Kappa.

## Results

1. **Kết quả đánh giá tự động:** Phương pháp ICL với prompt 7-shot đạt kết quả tự động cao nhất (ROUGE-L đạt 55.95, METEOR đạt 34.62, BERTScore đạt 75.92). ICL với prompt 5-shot đạt BLEU-4 cao nhất (22.87). RAG đơn lẻ có điểm số tự động tương đối thấp do việc truy xuất tài liệu bên ngoài đôi khi mang lại nội dung kém trực quan hoặc misaligned với đoạn văn gốc. Tuy nhiên, cả RAG và Hybrid Model đều vượt trội đáng kể so với các baseline fine-tuned (T5, BART).
2. **Kết quả đánh giá con người:** **Hybrid Model** đạt điểm số cao nhất và vượt trội hoàn toàn trên hầu hết các tiêu chí quan trọng nhất: Ngữ pháp (Gramm = 4.84), Sự phù hợp (Appr = 4.74), Độ liên quan ngữ cảnh (Rel = 4.25), và Độ phức tạp nhận thức (Complexity = 4.02). Mô hình ICL 7-shot dẫn đầu về tính dễ trả lời (Answ = 3.31 so với Hybrid là 3.20). Chỉ số Fleiss's Kappa đạt từ 0.45 đến 0.51 thể hiện sự đồng thuận ở mức trung bình khá (moderate agreement) giữa các giáo viên và học sinh.

## Limitations

- **Nhiễu từ mô-đun truy xuất:** RAG và Hybrid Model dễ bị ảnh hưởng nếu mô-đun FAISS truy xuất nhầm các tài liệu ngoài lề hoặc trùng lặp, làm giảm tính dễ trả lời của câu hỏi (Answerability).
- **Phạm vi ngữ cảnh giới hạn:** Thử nghiệm mới chỉ được thực hiện trên tập sách giáo khoa phổ thông NCERT của Ấn Độ với cấu trúc văn bản tương đối đơn giản, chưa đánh giá trên các giáo trình đại học phức tạp.
- **Thiếu kiểm duyệt trực tiếp:** Chưa có cơ chế tích hợp quy trình chỉnh sửa/duyệt trực tiếp của giáo viên trước khi xuất bản câu hỏi vào hệ thống LMS.

## Relevance to our topic

- Khẳng định mô hình lai **Hybrid (RAG kết hợp Prompt Few-shot)** là giải pháp tối ưu nhất cho hệ thống LMS sinh quiz bám sát slide/tài liệu bài học của nhóm chúng ta, giúp tạo ra các câu hỏi vừa giàu ngữ cảnh vừa có tính phức tạp nhận thức tốt.
- Cung cấp khung đánh giá sư phạm tiêu chuẩn (Rubric 5 tiêu chí: ngữ pháp, sự phù hợp, tính liên quan, độ phức tạp, khả năng trả lời) để áp dụng vào pha đánh giá thực nghiệm cho đề tài nghiên cứu.

## Possible improvement

- **Cải tiến mô-đun RAG nâng cao (Advanced RAG):** Thay vì FAISS cơ bản trên text thuần, chúng ta có thể áp dụng cơ chế Chunking theo cấu trúc slide và tích hợp Re-ranking để tăng độ chính xác của thông tin truy xuất, giảm nhiễu.
- **Cá nhân hóa theo chuẩn đầu ra (CLO):** Điều chỉnh các ví dụ few-shot trong prompt của Hybrid Model sao cho phản ánh trực tiếp các cấp độ nhận thức tương ứng với chuẩn đầu ra môn học (CLO) cần đánh giá.
