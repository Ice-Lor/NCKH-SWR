# BẢN ĐỀ XUẤT ĐỀ TÀI (TOPIC PROPOSAL)

## 1. Tên đề tài dự kiến (Proposed Topic Name)

- **Tiếng Anh:** An AI-Powered Decision Support System for Automated Resume Screening and Candidate Recommendation.
- **Tiếng Việt:** Hệ thống hỗ trợ ra quyết định ứng dụng trí tuệ nhân tạo trong tự động sàng lọc hồ sơ và gợi ý ứng viên.

## 2. Lĩnh vực ứng dụng (Application Domain)

Lĩnh vực Quản trị nhân sự (Human Resource Management - HRM) và quy trình Tuyển dụng tài năng (Talent Acquisition) tại các doanh nghiệp, công ty.

## 3. Vấn đề thực tế (Real-world Problem)

Trong các đợt tuyển dụng, bộ phận nhân sự (HR) tại các doanh nghiệp luôn đối mặt với những thách thức lớn:

- **Chi phí nhân sự và vận hành cao cho các tác vụ lặp lại:** Doanh nghiệp phải tiêu tốn một khoản ngân sách lớn để duy trì đội ngũ chuyên viên tuyển dụng chỉ để thực hiện các quy trình mang tính thủ tục và lặp đi lặp lại liên tục (nhận JD → đăng tin tuyển dụng → lọc CV sơ bộ → gửi email hẹn phỏng vấn...). Việc này gây lãng phí lớn về mặt tài chính nhưng đem lại hiệu suất tối ưu thấp.
- **Quá tải hồ sơ và tốn thời gian:** Số lượng CV đổ về quá lớn khiến HR mất nhiều thời gian và công sức để đọc, sàng lọc thủ công, dẫn đến kéo dài quy trình và dễ bỏ lỡ các ứng viên tiềm năng do phản hồi chậm.
- **Hạn chế của công cụ cũ (ATS):** Các hệ thống lọc CV truyền thống chỉ tìm kiếm theo từ khóa thô (Keyword-matching). Nếu ứng viên dùng từ đồng nghĩa hoặc cách diễn đạt khác, hệ thống cũ sẽ bỏ sót nhân tài.
- **Lãng phí tài nguyên dữ liệu cũ:** Doanh nghiệp thường "bỏ quên" và không có công cụ khai thác lại kho dữ liệu ứng viên tiềm năng (Talent Pool) từ các đợt tuyển dụng trước khi có dự án mới cần người gấp.

## 4. Đối tượng người dùng (Target Users)

- **Chuyên viên tuyển dụng (HR Recruiters):** Người trực tiếp cần công cụ tự động hóa các tác vụ lặp lại và xếp hạng CV nhanh chóng.
- **Trưởng phòng ban / Quản lý dự án (Hiring Managers):** Người cần tìm kiếm nhân sự phù hợp cho dự án của mình từ kho dữ liệu cũ và cần xem đánh giá sơ bộ của ứng viên.
- **Giám đốc nhân sự (HR Managers):** Người sử dụng các báo cáo, số liệu phân tích từ hệ thống để đưa ra quyết định tuyển dụng cuối cùng nhằm tối ưu chi phí doanh nghiệp.

## 5. Lý do cần tích hợp AI (Reason for AI Integration)

- **Tối ưu hóa chi phí và nguồn lực:** Thay thế các tác vụ thủ công, lặp đi lặp lại bằng các module tự động, giúp giải phóng sức lao động của đội ngũ HR để họ tập trung vào các công việc chiến lược có giá trị cao hơn (như phỏng vấn chuyên sâu, xây dựng văn hóa doanh nghiệp).
- **Hiểu văn cảnh ngữ nghĩa:** AI có khả năng hiểu sâu ý nghĩa của từ ngữ (Semantic understanding) trong CV và JD, giúp đánh giá độ phù hợp một cách thông minh thay vì chỉ đếm từ khóa.
- **Truy xuất tri thức nội bộ:** Giúp kết nối và tái khai thác thông minh nguồn dữ liệu ứng viên khổng lồ vốn đã bị lưu kho lâu ngày của doanh nghiệp.

## 6. Model AI dự kiến sử dụng (Intended AI Models)

Hệ thống dự kiến tích hợp các công nghệ và mô hình AI bao gồm:

- **Semantic Embedding Models:** Các mô hình nhúng văn bản (như `text-embedding-004` của Google hoặc mã nguồn mở như `bge-large`) để chuyển đổi CV/JD sang Vector phục vụ so khớp ngữ nghĩa.
- **Vector Database (ChromaDB):** Dùng để lưu trữ các Vector hồ sơ phục vụ tìm kiếm siêu nhanh.
- **Large Language Models (LLMs):** Sử dụng `Gemini 1.5 Flash / Pro` qua API để triển khai kiến trúc RAG (gợi ý ứng viên từ kho dữ liệu) và đóng vai trò "Trợ lý ảo" nhận xét câu trả lời phỏng vấn sơ bộ.

## 7. Kết quả mong muốn (Expected Results)

- **Về mặt kỹ thuật:** Xây dựng thành công một bản ứng dụng chạy thử nghiệm (Prototype) tích hợp mượt mà các module AI (Tự động hóa đăng tuyển, Sàng lọc, Gợi ý, Đánh giá tình huống).
- **Về mặt thực nghiệm:** Thu thập bộ dữ liệu gồm 5-10 JD và 50-100 CV giả lập để chạy thử nghiệm. Chứng minh hệ thống AI đạt độ chính xác cao (Precision, Recall, F1-Score) khi đối chiếu với kết quả chấm từ chuyên gia HR con người.
- **Về mặt học thuật:** Hoàn thiện một bài báo khoa học (Conference Paper) dày dặn, đúng chuẩn cấu trúc nghiên cứu hệ thống để nộp hội thảo.
