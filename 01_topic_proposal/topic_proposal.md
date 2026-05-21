# 1. Group Information
- Class: SE2037

- Group:7

- Leader: SE201597 - Quãng Sĩ Hưng 

- Members: 
 + SE201564- Nguyễn Đặng Quốc Bảo
 + SE201211- Phan Tấn Tài
 + SE200436- Phạm Quốc Duy
 + SE194262- Lê Minh Quân 
 + SE203024- Nguyễn Hữu Thành

# 2. Proposed Title
- English title: AI-Driven Personal Assistant for Mitigating Academic Procrastination and Enhancing Time Management among Students

- Vietnamese title: Xây dựng ứng dụng trợ lý ảo cá nhân ứng dụng Trí tuệ nhân tạo nhằm giảm thiểu hành vi trì hoãn học tập và nâng cao năng lực quản lý thời gian cho học sinh, sinh viên

# 3. Application Domain
+ Education (Quản lý học tập)

+ Student support (Hỗ trợ người dùng cá nhân)

# 4. Problem Statement
- Sự bùng nổ của các nền tảng video ngắn (TikTok, Facebook Reels, YouTube Shorts) tạo ra cơ chế nhận phần thưởng ngắn hạn (Dopamine hit), khiến thế hệ học sinh, sinh viên ngày nay có xu hướng giảm khả năng tập trung (Attention span) và dễ rơi vào hội chứng trì hoãn kinh niên (Chronic procrastination). Sinh viên thường xuyên nước đến chân mới nhảy, dẫn đến tình trạng stress, thức đêm nộp bài muộn và suy giảm nghiêm trọng kết quả học tập. Các công cụ quản lý thời gian truyền thống (như ứng dụng Pomodoro tĩnh, To-do list) hiện nay quá khô khan, thiếu tính linh hoạt và dễ dàng bị người học ngó lơ hoặc tắt đi khi họ cảm thấy lười biếng.

# 5. Motivation
- Vấn đề xao nhãng và trì hoãn ảnh hưởng trực tiếp đến chất lượng đầu ra của giáo dục đại học. Việc giải quyết bài toán này không chỉ giúp sinh viên cải thiện điểm số (GPA) mà còn hình thành kỹ năng quản lý thời gian – một trong những kỹ năng mềm cốt lõi khi đi làm. Việc tích hợp AI đóng vai trò như một giải pháp mang tính bước ngoặt: thay vì ép buộc một cách máy móc, AI có thể đóng vai trò như một "Huấn luyện viên tâm lý" hiểu được hành vi, thói quen và cảm xúc của từng sinh viên để đưa ra những can thiệp kịp thời, tinh tế và mang tính cá nhân hóa cao.

# 6. Target Users
-Học sinh, sinh viên: Đối tượng trực tiếp tương tác với hệ thống để quản lý lịch học, trò chuyện giải tỏa áp lực và rèn luyện tính kỷ luật.


# 7. Proposed AI Model / Method
- LLM (Large Language Model): Sử dụng API của các mô hình như GPT-4o-mini hoặc tinh chỉnh các mô hình mã nguồn mở như Llama 3 (hoặc PhoBERT cho Tiếng Việt) để xây dựng Chatbot thông minh, đóng vai trò người bạn đồng hành tâm lý giao tiếp bằng ngôn ngữ tự nhiên.

- RAG (Retrieval-Augmented Generation): Kết hợp RAG với cơ sở dữ liệu về tâm lý học hành vi (Behavioral Psychology) và các phương pháp khoa học (như Pomodoro, quy tắc 5 phút) để đảm bảo Chatbot đưa ra lời khuyên chuẩn xác, không bị "ảo tưởng" (hallucination).

- Classification / Regression model (XGBoost / Random Forest): Sử dụng để phân tích dữ liệu lịch sử sử dụng app của sinh viên nhằm dự đoán "Chỉ số nguy cơ trì hoãn" (Procrastination Risk Score) trong ngày.

# 8. System Features
Các chức năng chính của hệ thống:

1. Chatbot Trợ lý Tâm lý AI (AI Mental Coach): Cho phép sinh viên tâm sự về trạng thái học tập (ví dụ: "Hôm nay mình nản quá"), AI sẽ phân tích tâm trạng và đề xuất cách chia nhỏ bài tập, thương lượng lộ trình học phù hợp thay vì ép buộc.

2. Quản lý phiên học tập thông minh (Smart Pomodoro): Tích hợp tính năng Game hóa (Gamification). Khi bắt đầu học, hệ thống sẽ theo dõi việc thoát ứng dụng hoặc chuyển tab. Nếu phát hiện xao nhãng, AI sẽ gửi thông báo nhắc nhở "hài hước/tinh tế" để kéo sinh viên quay lại.

3. Phân tích và Dự đoán hành vi (Behavioral Analytics Dashboard): Thống kê thời gian tập trung, biểu đồ các khung giờ sinh viên hay lười nhất, từ đó AI tự động đề xuất lịch trình học tối ưu cá nhân hóa cho tuần kế tiếp.

4. Hệ thống Nhiệm vụ và Phần thưởng (Quest & Reward System): Biến việc hoàn thành bài tập thành các nhiệm vụ trong game để tích điểm nuôi thú ảo hoặc thăng hạng, tạo động lực duy trì thói quen bền vững.

# 9. Expected Contribution
Đóng góp dự kiến:

1. > Về mặt công nghệ: Ứng dụng thành công sự kết hợp giữa LLM, RAG và mô hình dự đoán hành vi vào một sản phẩm EdTech thực tế cho sinh viên Việt Nam.

2. > Về mặt thực tiễn: Tạo ra một công cụ hỗ trợ cải thiện rõ rệt thời gian tự học trung bình và giảm tỷ lệ trễ hạn (late submission) bài tập của sinh viên tham gia thử nghiệm.

3. > Về mặt khoa học: Đóng góp một bộ dữ liệu (đã ẩn danh) về hành vi học tập và các mô thức trì hoãn của sinh viên trong kỷ nguyên số, phục vụ cho các nghiên cứu giáo dục tương lai.

# 10. Evaluation Plan
Nhóm sẽ đánh giá hệ thống như thế nào?

- Dataset: Sử dụng tập dữ liệu tự thu thập từ quá trình chạy thử nghiệm (Beta testing) với một nhóm khoảng 50-100 sinh viên trong vòng 3 tuần (bao gồm nhật ký chat, thời gian học, tần suất xao nhãng).

- Baseline: So sánh hiệu quả tập trung của sinh viên khi dùng ứng dụng AI này với khi họ sử dụng phương pháp đếm giờ Pomodoro truyền thống (hoặc không dùng công cụ hỗ trợ).

- Metrics:

+ Hệ thống AI: Sử dụng F1-score/Accuracy để đánh giá mô hình dự đoán nguy cơ trì hoãn; dùng BLEU/ROUGE hoặc đánh giá từ con người để đo lường chất lượng phản hồi của Chatbot.

+ Hiệu quả người dùng: Đo lường bằng Tổng thời gian tập trung (Focus hours), Tỷ lệ hoàn thành mục tiêu ngày (Task completion rate), và Điểm giảm mức độ trì hoãn qua thang đo tâm lý (Pure Procrastination Scale - PPS).

- Expert evaluation: Xin ý kiến đánh giá từ các giảng viên khoa Tâm lý học hoặc Cố vấn học tập về tính đúng đắn của các lời khuyên định hướng hành vi mà AI đưa ra.

- User survey: Thực hiện khảo sát dựa trên mô hình TAM (Technology Acceptance Model) để đánh giá độ hài lòng, tính dễ sử dụng và tính hữu ích của ứng dụng đối với sinh viên.

# 11. Related Papers



| No | Title | Year | Source | Link / DOI |
|---|---|---|---|---|
| 1 | Academic procrastination and mobile phone addiction among college students: The mediating role of bedtime procrastination|2021 |Journal of Affective Disorders (Elsevier) |https://doi.org/10.1016/j.jad.2021.07.032|
| 2 |Systematic review of research on artificial intelligence applications in higher education – where are the educators? |2019 | International Journal of Educational Technology in Higher Education (Springer)|https://doi.org/10.1186/s41239-019-0171-0 |
| 3 |Predictive models for student procrastination in online learning environments Using Machine Learning |2022|Education and Information Technologies (Springer)|https://doi.org/10.1007/s10639-022-11105-z |
| 4 | Leveraging Large Language Models for Conversational Agents in Intelligent Tutoring Systems| 2024| Computers and Education: Artificial Intelligence (Elsevier)| https://doi.org/10.1016/j.caeai.2024.100215|
| 5 | Designing conversational Agents for adaptive instructional support in business simulation gaming| 2023|ScienceDirect. |https://www.sciencedirect.com/science/article/pii/S2666920X2600038X |