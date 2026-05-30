# Paper 03 Summary

## Citation

- **Tên bài báo:** Enhancing Automated Exam Creation with Retrieval-Augmented Generation for Scalable Educational Assessment
- **Tác giả:** Charaf Hamidi, Mohamed Badiy, Salma Gaou, Fatima Amounas, Mourade Azrour, Hicham Tribak, Abdullah M. Alnajim, Abdulatif Alabdulatif
- **Năm:** 2025
- **Nguồn:** Journal of Advances in Information Technology (JAIT), Vol. 16, No. 10
- **Link / DOI:** 10.12720/jait.16.10.1430-1441

## Problem

Nghiên cứu giải quyết bài toán tự động hóa quy trình soạn đề thi trắc nghiệm và câu hỏi mở có độ chính xác ngữ cảnh cao, đáp ứng nhu cầu sư phạm và giảm tải khối lượng công việc cho giảng viên. Soạn đề thủ công tốn rất nhiều thời gian. Trong khi đó, các phương pháp tạo đề bằng LLM thuần túy không có RAG thường dễ xảy ra lỗi ảo giác (hallucination) và thiếu chính xác thực tế, đặc biệt là với các chủ đề yêu cầu tính chặt chẽ kỹ thuật như cú pháp SQL, và đối với các ngôn ngữ không phải tiếng Anh (trong bài báo này là tiếng Pháp).

## Method

Nhóm nghiên cứu phát triển một hệ thống sinh đề thi SQL tự động bằng tiếng Pháp dựa trên RAG với kiến trúc 4 thành phần chính:
1. **Curated Knowledge Base (Cơ sở tri thức chọn lọc):** Xây dựng từ các tài liệu PDF giảng dạy SQL tiếng Pháp được thu thập tự động và trích xuất text bằng LLaMAParse. Văn bản được chia nhỏ (chunking) bằng MarkdownTextSplitter và gộp các chunk < 300 từ để tránh phân mảnh ngữ cảnh.
2. **Advanced RAG Pipeline (Pipeline truy xuất nâng cao):** 
   - Vector hóa văn bản bằng mô hình embedding tương thích tiếng Pháp: `all-MPNet-base-v2`.
   - Lưu trữ và tìm kiếm tương tự bằng FAISS để truy xuất top $k=25$ chunks.
   - Áp dụng bước lọc nhiễu (loại bỏ TOC, ellipses, các đoạn văn < 30 từ) và xếp hạng lại bằng mô hình zero-shot classification `facebook/bart-large-mnli` để giữ lại các chunk liên quan nhất.
3. **NLP-driven Question Generation (Sinh câu hỏi bằng LLM):** Sử dụng LLaMA 3.2 (chạy local qua OLLaMA) để sinh câu hỏi trắc nghiệm (MCQ) hoặc câu hỏi mở bám sát một JSON Schema nghiêm ngặt. Hệ thống cho phép chọn 3 cấp độ khó: "débutant" (sơ cấp), "intermédiaire" (trung cấp), "avancé" (cao cấp) căn chỉnh theo Bloom Taxonomy.
4. **Interactive UI (Giao diện Next.js):** Giao diện thân thiện dành cho giảng viên để cấu hình đề thi, chỉnh sửa/phê duyệt câu hỏi sinh ra (Human-in-the-loop), cho phép sinh viên làm bài và xem phản hồi chấm điểm thời gian thực.

## Dataset

- **Nguồn tài liệu:** 120 tài liệu PDF giáo trình và bài tập SQL tiếng Pháp được cào tự động từ các nguồn mở (Open Access). 
- **Kết quả lọc:** Loại bỏ các file lỗi/bị khóa bản quyền, giữ lại **102 PDF chất lượng** (~75MB văn bản sạch sau khi trích xuất) tương đương khoảng **2,520 chunks**.
- **Phân bổ chủ đề:** SQL Joins (30%), Transactions (25%), Sub-queries (20%), và các chủ đề khác (25%).

## Evaluation

Hệ thống được đánh giá toàn diện qua:
1. **Hiệu năng kỹ thuật:** Đo lường thời gian truy xuất của FAISS và độ chính xác tìm kiếm (Precision@5). So sánh hiệu quả trước và sau khi tích hợp mô hình Re-ranking.
2. **Đánh giá chuyên gia (Expert Validation):** Các giảng viên CNTT và chuyên gia SQL (bao gồm chính các tác giả có chứng chỉ SQL) kiểm duyệt chất lượng câu hỏi, tính đúng đắn của cú pháp SQL và độ căn chỉnh mức khó.
3. **Khảo sát thực nghiệm lớp học (Classroom Usability):** Triển khai ứng dụng Next.js cho một nhóm nhỏ sinh viên CNTT học môn SQL trải nghiệm thực tế và lấy ý kiến khảo sát của giảng viên về lượng thời gian tiết kiệm được.

## Results

1. **Hiệu năng kỹ thuật:** Thời gian truy xuất trung bình cực kỳ nhanh, đạt 0.6 giây dưới tải bình thường. Mô hình FAISS đạt độ chính xác Precision@5 là 85%. Việc bổ sung mô hình Re-ranking bằng BART giúp cải thiện từ 8% đến 12% chất lượng của top 5 chunks được chọn, giúp loại bỏ hiệu quả các phần nhiễu.
2. **Hiệu quả thực tế:** Pilot test thực tế cho thấy hệ thống vận hành ổn định. Giảng viên đánh giá hệ thống giúp **giảm 38% thời gian soạn đề thi** nhờ việc chỉnh sửa trên các câu hỏi được gợi ý sẵn thay vì soạn thảo từ đầu. Các câu hỏi SQL tiếng Pháp sinh ra có cú pháp chuẩn xác và bám sát tài liệu học tập.

## Limitations

- **Giới hạn ngôn ngữ và chủ đề:** Hệ thống hiện tại chỉ được cấu hình tối ưu để tạo đề thi SQL bằng tiếng Pháp.
- **Quy mô thực nghiệm nhỏ:** Đánh giá thực nghiệm mới dừng lại ở quy mô một lớp học công nghệ thông tin nhỏ, chưa kiểm chứng diện rộng ở nhiều môn học và khoa ngành khác nhau.
- **Thiếu framework đánh giá tự động:** Chất lượng câu hỏi sinh ra chưa được kiểm chứng độ chính xác tự động thông qua các framework đánh giá RAG tiêu chuẩn (như Ragas).

## Relevance to our topic

- Cung cấp mô hình tham chiếu thực tế để thiết kế giao diện web LMS (tương tự Next.js/FastAPI) có tích hợp chức năng cho giảng viên phê duyệt/chỉnh sửa câu hỏi (Human-in-the-loop).
- Kỹ thuật nâng cao như làm sạch chunk (chunk cleaning) và xếp hạng lại bằng mô hình phân loại zero-shot (Re-ranking) rất hữu ích để cải thiện độ chính xác cho RAG pipeline trong đề tài SWR.

## Possible improvement

- **Tích hợp module giải thích chi tiết:** Bổ sung chức năng tự động tạo phản hồi giải thích chi tiết (detailed feedback) cho từng câu hỏi dựa trên các slide bài giảng được định vị qua RAG để hỗ trợ học sinh tự học hiệu quả hơn.
- **Mở rộng đa ngôn ngữ và đa môn học:** Cấu hình prompt và cơ sở tri thức để hệ thống có thể tạo sinh câu hỏi đa lĩnh vực bằng tiếng Việt/tiếng Anh bám sát chuẩn đầu ra CLO.
