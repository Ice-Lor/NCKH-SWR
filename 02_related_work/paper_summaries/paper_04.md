# Paper 04 Summary

## Citation

- **Tên bài báo:** Generating In-Context, Personalized Feedback for Intelligent Tutors with Large Language Models
- **Tác giả:** Jennifer M. Reddig, Arav Arora, Christopher J. MacLellan
- **Năm:** 2025
- **Nguồn:** International Journal of Artificial Intelligence in Education (Springer)
- **Link / DOI:** https://doi.org/10.1007/s40593-025-00505-6

## Problem

Nghiên cứu tập trung vào vấn đề sinh phản hồi sửa lỗi cá nhân hóa (personalized corrective feedback) trong các hệ thống gia sư thông minh (Intelligent Tutoring Systems - ITS). Để phản hồi có tác dụng nâng cao kết quả học tập, nó cần được điều chỉnh chính xác theo lỗi sai cụ thể của học sinh. Tuy nhiên, việc thiết lập các luật lỗi (bug rules) thủ công rất tốn thời gian, chi phí cao và thiếu linh hoạt trước các hành vi bất ngờ của học sinh. Việc sử dụng LLM thuần túy để giải toán và tạo feedback trực tiếp dễ dẫn đến hiện tượng ảo giác và hướng dẫn sai lệch cho người học.

## Method

Nhóm nghiên cứu đề xuất giải pháp tích hợp LLM (cụ thể là GPT-4) vào nền tảng ITS **Apprentice Tutors** để tự động hóa chẩn đoán lỗi và tạo phản hồi:
1. **Phân loại lỗi quy nạp:** Phân tích dữ liệu lỗi của học sinh và phân loại thành 5 nhóm:
   - *Logical Mistake (Lỗi logic):* Áp dụng sai quy tắc, thực hiện sai phép tính.
   - *Syntax Error (Lỗi cú pháp):* Gõ nhầm ký tự, định dạng không chuẩn.
   - *Incomplete (Chưa hoàn thành):* Thoát ô nhập khi chưa viết xong đáp án.
   - *Wrong Field (Sai vị trí):* Nhập đáp án đúng của bước khác vào ô này.
   - *Correct Answer (Đáp án đúng):* Đáp án đúng nhưng hệ thống ghi nhận lỗi do lỗi tích lũy từ bước trước.
2. **Prompt chẩn đoán & tạo feedback:** Sử dụng prompt có cấu trúc Chain-of-Thought (CoT), cung cấp cho GPT-4 các thông tin ngữ cảnh của ITS gồm: đầu vào của học sinh, đáp án mong muốn, giao diện gia sư, kỹ năng đang học và ước lượng độ thành thạo kỹ năng (BKT estimate). GPT-4 được yêu cầu mô tả lỗi sai trước, sau đó mới viết hint sửa lỗi.
3. **Đánh giá tự động bằng học sinh giả lập (Simulated Student):** Sử dụng LLM đóng vai học sinh ảo để tương tác với hệ thống dựa trên hint được tạo ra, nhằm đo lường xem học sinh có thể tự sửa sai và tìm ra đáp án đúng hay không.

## Dataset

- Sử dụng dữ liệu thực tế thu thập từ sinh viên học lớp Đại số Đại học (College Algebra) học kỳ Spring 2024 trên hệ thống Apprentice Tutors.
- Tổng số giao dịch ghi nhận: **6,926 giao dịch học tập**.
- Số giao dịch lỗi được dùng để sinh feedback: **1,307 câu trả lời sai**.

## Evaluation

Nghiên cứu thực hiện đánh giá qua ba câu hỏi nghiên cứu (RQs):
1. **Đánh giá khả năng chẩn đoán lỗi:** So sánh kết quả chẩn đoán lỗi tự động của GPT-4 với kết quả phân tích thủ công của 2 chuyên gia (đo độ chính xác và chỉ số đồng thuận Cohen's Kappa, đạt 0.931).
2. **Đánh giá con người về chất lượng feedback:** Chuyên gia giáo dục đánh giá trực quan các hint được tạo ra về tính liên quan, độ chi tiết và tính sư phạm.
3. **Đánh giá tự động chất lượng feedback:** Đo tỷ lệ học sinh giả lập (simulated student) có thể tự giải đúng bài toán sau khi nhận hint từ LLM.

## Results

1. **Khả năng chẩn đoán lỗi:** GPT-4 chẩn đoán lỗi sai của học sinh đạt độ chính xác **khoảng 80%** đối với các lỗi đơn lẻ. Độ chính xác giảm đáng kể khi câu trả lời của học sinh chứa đồng thời nhiều lỗi phức tạp (>1 lỗi).
2. **Chất lượng phản hồi sửa lỗi:** Phần lớn hints tạo ra có tính cá nhân hóa tốt. Tuy nhiên, **35% số hints bị đánh giá lỗi** do quá chung chung, giải thích sai kiến thức, hoặc trực tiếp làm lộ đáp án đúng (bottom-out hint), làm mất đi tính tự học của học sinh.
3. **Hiệu quả của học sinh giả lập:** Chỉ có **35% số feedback vượt qua** được bài kiểm tra độ hữu ích tự động của học sinh giả lập. Kết quả này chỉ ra rằng việc sử dụng LLM để tự động đánh giá và bộ lọc chất lượng feedback vẫn còn hạn chế lớn và chưa thể thay thế hoàn toàn con người.

## Limitations

- **Môn học có cấu trúc cao:** Thử nghiệm chỉ mới áp dụng trên môn Đại số Đại học (College Algebra), vốn là môn học có tính logic rất chặt chẽ và có lượng dữ liệu huấn luyện khổng lồ trong LLM, khó tổng quát hóa sang các môn học lý thuyết hoặc kỹ năng mềm.
- **Tỷ lệ feedback lỗi cao:** Tỷ lệ 35% hints bị lỗi hoặc lộ đáp án là quá lớn đối với một hệ thống giáo dục thực tế chạy tự động hoàn toàn.
- **Thiếu RAG:** Hệ thống hoàn toàn dựa trên prompt zero-shot/few-shot mà chưa tích hợp RAG để truy xuất tri thức nền từ tài liệu khóa học nhằm sinh phản hồi giải thích chính xác tuyệt đối.

## Relevance to our topic

- Cung cấp mô hình phân loại lỗi học sinh (đặc biệt là phân biệt lỗi logic, lỗi cú pháp và lỗi nhập sai trường) để thiết kế logic chẩn đoán lỗi trong hệ thống LMS của chúng ta.
- Chỉ ra rằng để hệ thống hoạt động thực tế, bắt buộc phải có cơ chế kiểm soát chất lượng phản hồi, hoặc tích hợp giao diện kiểm duyệt của giáo viên (Human-in-the-loop) để loại bỏ 35% câu trả lời lỗi.

## Possible improvement

- **Kết hợp RAG sinh Feedback:** Tích hợp RAG để truy xuất chính xác định nghĩa công thức hoặc phần slide bài giảng liên quan trực tiếp đến lỗi sai của học sinh. Việc này giúp LLM sinh phản hồi giải thích chuẩn xác 100% dựa trên tài liệu lớp học, loại bỏ hiện tượng feedback chung chung hoặc sai lệch.
- **Tối ưu hóa Prompt Feedback:** Áp dụng prompt theo cấu trúc định hình rõ ràng vai trò của Socratic Mentor để hướng dẫn học sinh tự tìm ra lỗi sai thay vì đưa ra đáp án trực tiếp.
