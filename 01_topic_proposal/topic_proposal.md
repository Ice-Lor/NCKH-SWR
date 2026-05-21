# Topic Proposal

## 1. Group Information

- **Class:**SE2037
- **Group:**04
- **Leader:**   Nguyễn Hoàng Anh Khoa
- **Members:**  Trần Anh Vinh
                Phan Phúc Thịnh
                Nguyễn Thị Quỳnh Trúc
                Nguyễn Quang Trường

---

## 2. Proposed Title

- **English title:**A Lightweight AI-Powered Learning Management System for Personalized Feedback and Quiz Generation in Software Engineering Education.
- **Vietnamese title:** Hệ Thống Quản Lí Giáo Dục dùng cho Cá nhân hóa Phản hồi và Xây dựng Quiz trong lĩnh vực giáo dục ngành Kĩ Thuật Phần Mềm 

---

## 3. Application Domain

* Education

---

## 4. Problem Statement

Trong môi trường giáo dục đại học, đặc biệt ở các môn học kỹ thuật phần mềm và công nghệ thông tin, giảng viên thường phải xử lý nhiều công việc lặp lại trong quá trình quản lý học tập như:

* Tạo quiz và câu hỏi luyện tập.
* Phản hồi bài làm của sinh viên.
* Theo dõi tiến độ học tập.
* Xác định sinh viên gặp khó khăn ở từng CLO.
* Gợi ý tài liệu học tập phù hợp.
* Hỗ trợ sinh viên tự học ngoài giờ.

Trong các hệ thống LMS truyền thống, phần lớn các công việc trên vẫn phụ thuộc nhiều vào thao tác thủ công của giảng viên.

Điều này dẫn đến nhiều vấn đề:

* Tốn thời gian tạo nội dung học tập.
* Khó cá nhân hóa việc học cho từng sinh viên.
* Sinh viên nhận phản hồi chậm.
* Khó theo dõi chính xác điểm yếu của từng người học.
* Chatbot hoặc hệ thống hỗ trợ hiện tại thường trả lời chung chung hoặc thiếu context của môn học.
* Nội dung AI sinh ra có thể không bám sát syllabus hoặc CLO.

Trong khi đó, các Large Language Models (LLMs) và Retrieval-Augmented Generation (RAG) hiện nay có khả năng:

* Sinh câu hỏi.
* Tạo phản hồi học tập.
* Tóm tắt tài liệu.
* Hỗ trợ hỏi đáp.
* Cá nhân hóa nội dung.

Tuy nhiên, việc tích hợp các mô hình AI này vào LMS theo hướng có ngữ cảnh học tập (course-aware) và đánh giá được hiệu quả thực tế vẫn còn hạn chế.

Do đó, nhóm đề xuất xây dựng:

> A Lightweight AI-Powered Learning Management System for Personalized Feedback and Quiz Generation in Software Engineering Education.

Hệ thống tập trung tích hợp:

* LLM.
* RAG.
* Embedding-based retrieval.
* CLO-aware quiz generation.
* Personalized learning feedback.

---

## 5. Motivation

Sự phát triển nhanh của Generative AI mở ra khả năng ứng dụng mạnh mẽ trong giáo dục đại học.

Tuy nhiên, nhiều hệ thống hiện tại vẫn gặp các hạn chế:

* Chưa tích hợp AI trực tiếp vào workflow học tập.
* Chỉ dùng chatbot đơn giản.
* Không gắn với CLO hoặc syllabus.
* Không hỗ trợ cá nhân hóa học tập.
* Không đánh giá được mức độ hữu ích của AI trong môi trường thật.

Trong các môn Software Engineering, lượng nội dung lớn cùng với số lượng sinh viên đông khiến giảng viên gặp khó khăn khi:

* Sinh quiz thường xuyên.
* Phản hồi chi tiết cho từng sinh viên.
* Theo dõi learning outcome.
* Gợi ý nội dung học tập phù hợp.

Một AI-powered LMS có khả năng:

* Sinh quiz theo từng topic.
* Tạo feedback cá nhân hóa.
* Truy xuất nội dung môn học bằng RAG.
* Theo dõi tiến độ học tập.
* Hỗ trợ hỏi đáp theo syllabus.

sẽ giúp:

* Giảm workload cho giảng viên.
* Tăng tốc độ phản hồi.
* Tăng mức độ tương tác học tập.
* Cải thiện khả năng tự học của sinh viên.
* Tăng khả năng cá nhân hóa học tập.

---

## 6. Target Users

| Student    | Làm quiz, hỏi đáp, xem feedback, học tập    |
| Instructor | Quản lý môn học, tạo quiz, theo dõi tiến độ |
| Admin      | Quản lý hệ thống và dữ liệu                 |

---

## 7. Proposed AI Model / Method

* LLM

---

## 8. System Features

Các chức năng chính của hệ thống:

### Student Features

* Đăng nhập và quản lý học tập.
* Làm quiz AI-generated.
* Xem feedback cá nhân hóa.
* Chat với AI learning assistant.
* Xem learning progress.
* Nhận gợi ý học tập.

---

### Instructor Features

* Quản lý khóa học.
* Upload syllabus, slide, textbook.
* Sinh quiz tự động.
* Kiểm tra CLO achievement.
* Xem learning analytics dashboard.
* Quản lý feedback.

---

### AI Features

* Quiz generation.
* Personalized feedback generation.
* RAG-based learning assistant.
* CLO-aware recommendation.
* Learning content retrieval.

---

## 9. Expected Contribution

Đóng góp dự kiến:

* A working prototype of an LLM+RAG system integrated into a web-based topic registration workflow.
* An empirical evaluation of topic matching accuracy and supervisor recommendation quality.
* A comparison with baseline methods (TF-IDF, keyword matching, manual assignment).
* Evidence of time reduction and improved student satisfaction compared to the traditional process.

---

## 10. Evaluation Plan

Nhóm sẽ đánh giá hệ thống như thế nào?

- **Dataset:** Simulated dataset of 100–200 past research topics with supervisor profiles (anonymized or synthetic)
- **Baseline:** TF-IDF + cosine similarity, keyword matching, manual selection
- **Metrics:** Top-k Accuracy, Precision@k, Recall@k, NDCG
- **User evaluation:** Survey with 10–20 students (SUS + satisfaction questionnaire)

---

## 11. Related Papers

Liệt kê ít nhất 5 bài báo liên quan.

| No | Title | Year | Source | Link / DOI |
|----|-------|------|--------|------------|
| 1  |       |      |        |            |
| 2  |       |      |        |            |
| 3  |       |      |        |            |
| 4  |       |      |        |            |
| 5  |       |      |        |            |
