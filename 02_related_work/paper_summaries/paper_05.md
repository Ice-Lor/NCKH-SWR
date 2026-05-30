# Paper 05 Summary

## Citation

- **Tên bài báo:** Automated Educational Question Generation at Different Bloom’s Skill Levels using Large Language Models: Strategies and Evaluation
- **Tác giả:** Nicy Scaria, Suma Dharani Chenna, Deepak Subramani
- **Năm:** 2024
- **Nguồn:** arXiv / Springer (Lecture Notes in Artificial Intelligence, volume 14830)
- **Link / DOI:** https://doi.org/10.1007/978-3-031-64299-9_12 / https://arxiv.org/abs/2408.04394

## Problem

Nghiên cứu tập trung vào bài toán tự động sinh câu hỏi kiểm tra (AEQG) bám sát các mức độ tư duy nhận thức khác nhau của Bloom Taxonomy (từ nhận biết đến sáng tạo) phục vụ cho giáo dục trực tuyến quy mô lớn. Việc thiết kế câu hỏi đa dạng và bám sát thang Bloom một cách thủ công tốn nhiều công sức của giáo viên. Hầu hết các hệ thống AQG trước đây thường chỉ tạo được câu hỏi ở bậc nhận thức thấp (ghi nhớ thông tin có sẵn trong văn bản) hoặc bị giới hạn bởi việc thiếu tập dữ liệu chất lượng cao để fine-tuning.

## Method

Nghiên cứu tiến hành đánh giá so sánh 5 mô hình ngôn ngữ lớn (LLM) khác nhau trên 5 chiến lược thiết kế prompt (prompt strategies - PS) để sinh câu hỏi trắc nghiệm/tự luận theo 6 bậc nhận thức Bloom (Remember, Understand, Apply, Analyze, Evaluate, Create) cho một khóa học Khoa học Dữ liệu (Data Science) bậc Cao học (gồm 17 chủ đề).
- **5 LLM được thử nghiệm:** Mistral 7B, Llama 2 70B, Palm 2, GPT-3.5, và GPT-4.
- **5 Chiến lược Prompting (độ phức tạp tăng dần):**
  - *PS1:* Prompt chỉ dẫn cơ bản (Simple prompt).
  - *PS2:* CoT prompt kết hợp định nghĩa chi tiết của từng mức độ Bloom.
  - *PS3:* CoT prompt kết hợp câu hỏi ví dụ mẫu của chuyên gia cho từng mức Bloom (few-shot).
  - *PS4:* CoT prompt kết hợp cả định nghĩa và câu hỏi ví dụ mẫu.
  - *PS5:* CoT prompt kết hợp định nghĩa, giải thích chi tiết và câu hỏi ví dụ mẫu (prompt cực kỳ dài).
- **Yêu cầu ngữ cảnh hóa:** LLM được yêu cầu lồng ghép các ví dụ thực tế liên quan đến Ấn Độ (Bollywood, nông nghiệp, giao thông) để tăng tính sinh động.
- **Đánh giá tự động không tham chiếu (Reference-free Evaluation):** Sử dụng Gemini Pro (temperature = 0) để đánh giá câu hỏi dựa trên chính rubric của chuyên gia. Đo độ đa dạng câu hỏi bằng chỉ số PINC score.

## Dataset

Tập dữ liệu tự xây dựng có tên là **DataScienceQ** chứa **2,550 câu hỏi** được tạo ra từ tổ hợp của 5 LLM, 5 chiến lược prompt trên 17 chủ đề Khoa học Dữ liệu (như Hồi quy tuyến tính, Prompt Engineering, v.v.).

## Evaluation

Chất lượng câu hỏi được đánh giá thông qua:
1. **Human Evaluation (Đánh giá của chuyên gia):** 2 giảng viên Khoa học Dữ liệu chấm điểm ngẫu nhiên dựa trên một Rubric phân cấp gồm 9 mục (Understandable, TopicRelated, Grammatical, Clear, Rephrase, Answerable, Central, WouldYouUseIt, Bloom'sLevel). Quá trình đánh giá được thiết kế dừng sớm (early stopping) nếu câu hỏi không vượt qua các tiêu chí cơ bản như tính dễ hiểu. Đo chỉ số Cohen's Kappa và Quadratic Weighted Kappa để đánh giá độ đồng thuận.
2. **LLM Evaluation (Đánh giá bằng LLM):** Gemini Pro chấm điểm câu hỏi theo cùng rubric trên để so sánh mức độ tương quan với con người.

## Results

1. **Chất lượng câu hỏi và tính tuân thủ Bloom:** Có **78% số câu hỏi** tạo ra được chuyên gia đánh giá đạt chất lượng cao (High Quality) và **65.56% câu hỏi** khớp chính xác với bậc Bloom yêu cầu. Điểm số đa dạng PINC trung bình đạt 0.92, chứng tỏ các câu hỏi được tạo ra rất phong phú và không bị trùng lặp cấu trúc từ ngữ.
2. **Hiệu năng của các mô hình:** GPT-4 và GPT-3.5 dẫn đầu cuộc thử nghiệm (GPT-4 đạt tỷ lệ chất lượng cao 89.02%, GPT-3.5 đạt 86.27%). Không có mối tương quan tuyến tính rõ rệt giữa kích thước mô hình và chất lượng (ví dụ Mistral 7B hoạt động tốt hơn Llama 2 70B trong một số prompt phức tạp).
3. **Ảnh hưởng của chiến lược Prompt:** Chất lượng câu hỏi tăng dần từ PS1 đến PS4. Chiến lược **PS4 (CoT + định nghĩa mức Bloom + ví dụ mẫu)** cho kết quả tối ưu nhất trên toàn bộ các mô hình. Tuy nhiên, prompt quá dài như **PS5 lại phản tác dụng**, khiến chất lượng và độ tuân thủ Bloom của các mô hình nhỏ (Mistral, Llama 2, Palm 2) giảm mạnh (tỷ lệ tuân thủ Bloom trung bình giảm từ 72% xuống còn 51%).
4. **Đánh giá tự động bằng LLM:** Điểm đánh giá của Gemini Pro có độ tương quan khá thấp với đánh giá của chuyên gia con người, chứng minh rằng LLM hiện tại chưa đủ tin cậy để tự động chấm điểm chất lượng câu hỏi giáo dục.

## Limitations

- **Thiếu RAG:** Nghiên cứu hoàn toàn dựa vào kiến thức nội tại của LLM mà không cung cấp tài liệu ngữ cảnh bên ngoài, dẫn đến nguy cơ ảo giác cao khi áp dụng vào các chủ đề chuyên sâu hoặc mới xuất hiện.
- **Độ chính xác ngôn ngữ địa phương kém:** Các mô hình mã nguồn mở (Mistral, Llama 2) tạo sinh văn bản tiếng Ấn Độ bị lỗi ngữ pháp và dịch thuật nghiêm trọng.

## Relevance to our topic

- Chứng minh tính khả thi của việc hướng dẫn LLM sinh câu hỏi bám sát các mức độ nhận thức của Bloom Taxonomy để đáp ứng chuẩn đầu ra CLO của môn học.
- Đưa ra bài học thực tiễn về thiết kế prompt: Áp dụng trực tiếp cấu trúc prompt PS4 (CoT + giải thích mức Bloom/CLO + ví dụ mẫu few-shot) cho hệ thống LMS sinh quiz.
- Kế thừa Rubric phân cấp 9 mục rất khoa học và cơ chế dừng sớm để tối ưu hóa quy trình đánh giá chất lượng câu hỏi của giảng viên.

## Possible improvement

- **Tích hợp RAG:** Kết hợp tài liệu slide khóa học thông qua RAG với prompt chiến lược PS4 để đảm bảo câu hỏi vừa bám sát nhận thức Bloom, vừa đảm bảo tính chính xác tuyệt đối theo bài học thực tế trên lớp, loại bỏ hoàn toàn ảo giác.
- **Tự động sinh phản hồi sửa lỗi:** Mở rộng hệ thống để sinh phản hồi giải thích đáp án sai dựa trên các mức độ nhận thức tương ứng của Bloom.
