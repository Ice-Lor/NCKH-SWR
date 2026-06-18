# README - Quy trình làm bài báo Literature Review theo nhóm trên Git

## 1. Mục tiêu của repository

Repository này được sử dụng để quản lý quá trình học tập, nghiên cứu và viết bài báo theo nhóm trong các môn học.

Mỗi nhóm sinh viên sẽ làm việc trên **một nhánh Git riêng**, dùng để:

- Phác thảo ý tưởng đề tài.
- Tìm và phân tích bài báo liên quan.
- Tổng hợp literature review theo lĩnh vực.
- Viết abstract bài báo.
- Cập nhật tiến độ thường xuyên.
- Lưu minh chứng: tài liệu, bảng phân tích, báo cáo tuần.

Nhánh `main` chỉ dùng để lưu:

- Hướng dẫn chung.
- Template viết bài.
- Quy định đặt tên nhánh.
- Quy trình làm việc.
- Checklist đánh giá.
- Tài liệu tham khảo chung.

Các nhóm **không được viết trực tiếp lên nhánh `main`** nếu không được giảng viên cho phép.

---

## 2. Định hướng nghiên cứu

Các nhóm tập trung vào các lĩnh vực sau và ứng dụng của chúng trong thực tiễn:

- **Software Requirements Engineering**: elicitation, specification, validation, traceability, requirements management.
- **Business Analysis (BA)**: stakeholder analysis, process modeling, business process improvement, gap analysis.
- **Agile & Scrum**: sprint planning, retrospectives, agile adoption, scaling agile (SAFe, LeSS), agile metrics.
- **Các chủ đề liên quan**: user story, use case, acceptance criteria, product backlog, change management, process maturity (CMMI, SPICE).
- **Ứng dụng trong đời sống thực tế**: áp dụng các phương pháp trên trong giáo dục, doanh nghiệp vừa và nhỏ, chính phủ điện tử, startup, v.v.

> **Lưu ý:** Các nhóm **không** nghiên cứu về model AI hay xây dựng hệ thống AI. Trọng tâm là quy trình, phương pháp, và con người trong phát triển phần mềm và phân tích nghiệp vụ.

---

## 3. Mô hình tổ chức Git

Repository gồm 2 loại nhánh chính:

```text
main
│
├── SE1701_G01
├── SE1701_G02
├── SE1702_G01
├── SE1702_G02
└── ...
```

Trong đó:

- `main`: nhánh hướng dẫn chung.
- Mỗi nhóm có một nhánh riêng.
- Leader nhóm được cấp quyền quản lý nhánh của nhóm.
- Thành viên trong nhóm commit nội dung vào nhánh nhóm.
- Giảng viên theo dõi tiến độ qua lịch sử commit, pull request hoặc báo cáo tuần.

---

## 4. Quy định đặt tên nhánh

### 4.1. Cú pháp đặt tên

```text
<MA_LOP>_G<SO_THU_TU_NHOM>
```

Ví dụ:

```text
SE1701_G01
SE1701_G02
SE1702_G01
BDT301_G03
```

### 4.2. Quy tắc

| Thành phần | Ý nghĩa | Ví dụ |
|---|---|---|
| `MA_LOP` | Mã lớp hoặc mã môn/lớp | `SE1701`, `BDT301` |
| `G` | Viết tắt của Group | `G` |
| `SO_THU_TU_NHOM` | Số thứ tự nhóm, dùng 2 chữ số | `01`, `02`, `03` |

### 4.3. Ví dụ đúng

```text
SE1701_G01
SE1701_G02
BDT301_G05
SWR101_G03
```

### 4.4. Ví dụ không đúng

```text
Group1
Nhom1
SE1701_Nhom1
SE1701_Group_1
se1701_g1
```

---

## 5. Quy định phân quyền

### 5.1. Giảng viên

Giảng viên có quyền:

- Quản lý repository.
- Tạo hoặc duyệt nhánh nhóm.
- Kiểm tra tiến độ.
- Review nội dung.
- Comment góp ý.
- Merge nội dung tốt vào nhánh `main` nếu cần.

### 5.2. Leader nhóm

Leader nhóm có trách nhiệm:

- Quản lý nhánh của nhóm.
- **Phân công công việc cụ thể cho từng thành viên** và ghi rõ trong file phân công.
- Kiểm tra chất lượng nội dung trước khi commit.
- Đảm bảo nhóm cập nhật Git thường xuyên.
- Tạo pull request nếu giảng viên yêu cầu.
- Tổng hợp báo cáo tiến độ hằng tuần.

### 5.3. Thành viên nhóm

Thành viên nhóm có trách nhiệm:

- Làm đúng phần được phân công.
- Commit nội dung rõ ràng, có nội dung thật.
- Không xóa file của thành viên khác nếu chưa thống nhất.
- Ghi rõ nguồn tài liệu tham khảo.
- Cập nhật tiến độ đúng hạn.

---

## 6. Cách tạo nhánh nhóm

Leader hoặc giảng viên tạo nhánh theo cú pháp:

```bash
git checkout main
git pull origin main
git checkout -b SE1701_G01
git push -u origin SE1701_G01
```

Các thành viên clone repository:

```bash
git clone <repository-url>
cd <repository-name>
git checkout SE1701_G01
```

Cập nhật nội dung mới nhất từ nhánh nhóm:

```bash
git pull origin SE1701_G01
```

Commit nội dung:

```bash
git add .
git commit -m "docs: update research topic proposal"
git push origin SE1701_G01
```

---

## 7. Quy định commit message

Commit message nên viết rõ ràng theo cú pháp:

```text
<type>: <nội dung thay đổi>
```

### Loại commit thường dùng

| Type | Ý nghĩa | Ví dụ |
|---|---|---|
| `docs` | Cập nhật tài liệu | `docs: add related work summary` |
| `topic` | Cập nhật đề tài | `topic: refine research objectives` |
| `review` | Thêm phân tích bài báo | `review: analyze five related papers` |
| `matrix` | Cập nhật literature review matrix | `matrix: add comparison table` |
| `abstract` | Cập nhật abstract | `abstract: draft abstract v1` |
| `report` | Cập nhật báo cáo tuần | `report: add week 03 report` |
| `fix` | Sửa lỗi nội dung | `fix: correct citation format` |

Ví dụ:

```bash
git commit -m "review: summarize 5 papers on agile adoption in SMEs"
git commit -m "matrix: complete literature review matrix"
git commit -m "abstract: revise abstract based on feedback"
```

---

## 8. Cấu trúc thư mục đề xuất cho mỗi nhánh nhóm

Mỗi nhóm nên tổ chức thư mục như sau:

```text
.
├── README.md
├── 01_topic_proposal/
│   ├── topic_proposal.md
│   └── task_assignment.md
│
├── 02_related_work/
│   ├── search_keywords.md
│   ├── paper_list.md
│   ├── literature_review_matrix.md
│   └── paper_summaries/
│       ├── paper_01.md
│       ├── paper_02.md
│       └── paper_03.md
│
├── 03_problem_and_gap/
│   ├── problem_statement.md
│   ├── research_gap.md
│   └── research_questions.md
│
├── 04_abstract/
│   └── abstract.md
│
└── weekly_reports/
    ├── week_01.md
    ├── week_02.md
    ├── week_03.md
    ├── week_04.md
    ├── week_05.md
    └── week_06.md
```

---

## 9. Quy trình làm bài báo theo từng bước (6 tuần)

### Bước 1: Chọn đề tài và phân công (Tuần 1)

Mỗi nhóm chọn một chủ đề cụ thể trong các lĩnh vực định hướng, ví dụ:

- Thách thức trong thu thập yêu cầu phần mềm từ xa (remote requirements elicitation).
- Ứng dụng Agile/Scrum trong doanh nghiệp vừa và nhỏ tại Việt Nam.
- So sánh các phương pháp mô hình hóa quy trình nghiệp vụ (BPMN, UML, flowchart).
- Vai trò của Business Analyst trong các dự án chuyển đổi số.
- Quản lý product backlog hiệu quả trong môi trường Scrum.
- Đo lường chất lượng yêu cầu phần mềm (requirements quality metrics).
- Các yếu tố ảnh hưởng đến sự thành công của Agile adoption.

Kết quả cần tạo:

```text
01_topic_proposal/topic_proposal.md
01_topic_proposal/task_assignment.md
```

Nội dung `topic_proposal.md` cần có:

- Tên đề tài dự kiến (tiếng Anh và tiếng Việt).
- Lĩnh vực (SE Requirements / BA / Agile / ...).
- Vấn đề thực tế muốn tìm hiểu.
- Đối tượng liên quan (developer, BA, product owner, ...).
- Lý do chủ đề này quan trọng.
- Câu hỏi nghiên cứu dự kiến.

Nội dung `task_assignment.md` cần có:

- Danh sách thành viên và nhiệm vụ cụ thể từng người trong từng tuần.

---

### Bước 2: Tìm bài báo liên quan (Tuần 2)

Mỗi nhóm cần tìm tối thiểu:

- 5 bài báo liên quan trực tiếp đến chủ đề.
- 2 bài báo về bối cảnh thực tế (ứng dụng tại doanh nghiệp, ngành, khu vực).

Nguồn tìm kiếm đề xuất:

- Google Scholar.
- IEEE Xplore.
- ACM Digital Library.
- SpringerLink.
- ScienceDirect.
- MDPI.
- CEUR Workshop Proceedings.

Từ khóa tìm kiếm mẫu:

```text
software requirements elicitation challenges
agile adoption small medium enterprise
business analyst role digital transformation
product backlog management scrum
requirements quality metrics software project
BPMN business process modeling comparison
agile retrospective effectiveness
user story writing best practices
```

Kết quả cần tạo:

```text
02_related_work/search_keywords.md
02_related_work/paper_list.md
```

---

### Bước 3: Đọc và tóm tắt từng bài báo (Tuần 3)

Mỗi bài báo cần được tóm tắt theo mẫu:

```markdown
# Paper 01 Summary

## Citation

Tên bài:
Tác giả:
Năm:
Nguồn:
DOI/Link:

## Problem

Bài báo giải quyết vấn đề gì?

## Method

Bài báo dùng phương pháp nghiên cứu nào? (survey, case study, experiment, systematic literature review, ...)

## Context

Bài báo được thực hiện trong bối cảnh nào? (loại dự án, ngành, quy mô tổ chức, ...)

## Key Findings

Kết quả/phát hiện chính là gì?

## Limitations

Hạn chế của bài báo là gì?

## Relevance to our topic

Bài báo liên quan gì đến đề tài của nhóm?
```

Lưu tại:

```text
02_related_work/paper_summaries/paper_01.md
02_related_work/paper_summaries/paper_02.md
...
```

---

### Bước 4: Tạo Literature Review Matrix (Tuần 4)

Nhóm tổng hợp các bài báo thành bảng so sánh:

```markdown
| Paper | Year | Venue | Topic / Domain | Research Method | Context | Key Findings | Limitation | Relevance |
|---|---|---|---|---|---|---|---|---|
| Paper 1 | 2022 | IEEE | Agile adoption in SMEs | Survey | Vietnam SMEs | Lack of training is #1 barrier | Small sample | High |
| Paper 2 | 2021 | ACM | Requirements elicitation | Case study | Healthcare | Remote elicitation challenges | Single project | Medium |
```

Mục tiêu của bảng này:

- Biết các bài trước đã tìm hiểu vấn đề gì.
- Biết phương pháp nghiên cứu nào đã được dùng.
- Biết bối cảnh nào được nghiên cứu nhiều, bối cảnh nào còn thiếu.
- Tìm ra gap để định vị bài của nhóm.

Lưu tại:

```text
02_related_work/literature_review_matrix.md
```

---

### Bước 5: Xác định gap và câu hỏi nghiên cứu (Tuần 5)

Nhóm cần trả lời:

1. Chủ đề này đã được nghiên cứu ở đâu, như thế nào?
2. Còn thiếu nghiên cứu trong bối cảnh nào?
3. Vấn đề thực tế mà nhóm muốn làm rõ là gì?
4. Nhóm sẽ đặt ra những câu hỏi nghiên cứu nào?

Ví dụ gap:

> Các nghiên cứu về Agile adoption chủ yếu tập trung vào doanh nghiệp lớn tại các nước phát triển, trong khi ứng dụng Scrum trong các startup và doanh nghiệp vừa và nhỏ tại Đông Nam Á còn được khảo sát rất hạn chế.

Ví dụ câu hỏi nghiên cứu:

```text
RQ1. Những thách thức phổ biến nhất khi triển khai Scrum trong doanh nghiệp vừa và nhỏ là gì?

RQ2. Các yếu tố nào có tác động tích cực đến sự thành công của Agile adoption?

RQ3. Thực hành retrospective được áp dụng như thế nào trong các nhóm Scrum thực tế?
```

Kết quả cần tạo:

```text
03_problem_and_gap/problem_statement.md
03_problem_and_gap/research_gap.md
03_problem_and_gap/research_questions.md
```

---

### Bước 6: Viết Abstract (Tuần 6)

Đây là **sản phẩm cuối cùng** của nhóm trong học kỳ này.

Abstract cần được viết bằng **tiếng Anh**, khoảng 150–250 từ, và bao gồm đủ các thành phần:

| Thành phần | Nội dung cần thể hiện |
|---|---|
| Context / Motivation | Vì sao chủ đề này quan trọng? |
| Problem | Vấn đề hoặc gap còn tồn tại là gì? |
| Objective | Mục tiêu của bài báo là gì? |
| Method | Nhóm tiến hành nghiên cứu như thế nào? (literature review, systematic review, ...) |
| Key Findings | Phát hiện chính từ các bài báo đã phân tích. |
| Conclusion | Ý nghĩa và đóng góp của bài. |

Mẫu abstract:

```markdown
# Abstract

[Context] ... [Problem] ... [Objective] ... [Method] ... [Findings] ... [Conclusion] ...

**Keywords:** keyword1, keyword2, keyword3, keyword4, keyword5
```

Lưu tại:

```text
04_abstract/abstract.md
```

---

## 10. Mẫu file phân công nhiệm vụ

Tạo file:

```text
01_topic_proposal/task_assignment.md
```

Nội dung mẫu:

```markdown
# Task Assignment

## Group Information

- Class:
- Group:
- Leader:
- Members:

## Assignment Table

| Week | Task | Assigned To | Deadline | Status |
|---|---|---|---|---|
| Week 1 | Chọn đề tài và viết topic proposal | Nguyễn Văn A (Leader) | dd/mm/yyyy | Done |
| Week 1 | Tìm từ khóa tìm kiếm ban đầu | Trần Thị B | dd/mm/yyyy | Done |
| Week 2 | Tìm bài báo liên quan (5 bài) | Lê Văn C, Phạm Thị D | dd/mm/yyyy | In progress |
| Week 3 | Tóm tắt paper 1-3 | Trần Thị B | dd/mm/yyyy | Not started |
| Week 3 | Tóm tắt paper 4-5 | Lê Văn C | dd/mm/yyyy | Not started |
| Week 4 | Tạo literature review matrix | Nguyễn Văn A | dd/mm/yyyy | Not started |
| Week 5 | Viết problem statement và research gap | Phạm Thị D | dd/mm/yyyy | Not started |
| Week 6 | Viết abstract (bản nháp) | Cả nhóm | dd/mm/yyyy | Not started |
| Week 6 | Review và hoàn thiện abstract | Nguyễn Văn A (Leader) | dd/mm/yyyy | Not started |
```

---

## 11. Mẫu báo cáo tuần

Tạo file theo từng tuần:

```text
weekly_reports/week_01.md
weekly_reports/week_02.md
...
```

Nội dung mẫu:

```markdown
# Weekly Report - Week 01

## Group Information

- Class:
- Group:
- Leader:
- Members:

## Tasks Completed This Week

| Member | Task | Result |
|---|---|---|
| Nguyễn Văn A | Viết topic proposal | Hoàn thành |
| Trần Thị B | Tìm từ khóa tìm kiếm | Hoàn thành |
| Lê Văn C | Tìm 3 bài báo đầu tiên | Hoàn thành |

## Git Commits

| Commit ID | Message | Author |
|---|---|---|
| abc123 | topic: add topic proposal draft | Nguyen Van A |

## Current Problems

- Chưa thống nhất được phạm vi chủ đề.
- Chưa tìm đủ bài báo từ IEEE.

## Plan for Next Week

- Hoàn thiện topic proposal.
- Tìm đủ 7 bài báo liên quan.
- Viết search_keywords.md.

## Questions for Instructor

- Chủ đề X có thuộc phạm vi không?
- Bài survey có được tính là bài báo liên quan không?
```

---

## 12. Mẫu Topic Proposal

Tạo file:

```text
01_topic_proposal/topic_proposal.md
```

Nội dung mẫu:

```markdown
# Topic Proposal

## 1. Group Information

- Class:
- Group:
- Leader:
- Members:

## 2. Proposed Title

English title:

Vietnamese title:

## 3. Research Domain

Ví dụ: Software Requirements Engineering / Business Analysis / Agile & Scrum

## 4. Problem Statement

Mô tả vấn đề thực tế hoặc khoảng trống nghiên cứu mà nhóm muốn tìm hiểu.

## 5. Motivation

Vì sao chủ đề này quan trọng trong thực tiễn?

## 6. Target Context

Nghiên cứu này áp dụng cho đối tượng/bối cảnh nào? (loại tổ chức, quy mô, ngành, ...)

## 7. Preliminary Research Questions

RQ1.

RQ2.

RQ3.

## 8. Related Papers (preliminary)

Liệt kê ít nhất 3 bài báo liên quan đã tìm được ban đầu.

| No | Title | Year | Source | Link / DOI |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |
```

---

## 13. Mẫu Literature Review Matrix

Tạo file:

```text
02_related_work/literature_review_matrix.md
```

Nội dung mẫu:

```markdown
# Literature Review Matrix

| No | Paper Title | Year | Venue | Topic / Domain | Research Method | Context | Key Findings | Limitation | Relevance to Our Topic |
|---|---|---|---|---|---|---|---|---|---|
| 1 | | | | | | | | | |
| 2 | | | | | | | | | |
| 3 | | | | | | | | | |
| 4 | | | | | | | | | |
| 5 | | | | | | | | | |
```

---

## 14. Mẫu Abstract

Tạo file:

```text
04_abstract/abstract.md
```

Nội dung mẫu:

```markdown
# Abstract

## Draft Abstract

[Viết abstract tiếng Anh tại đây, 150-250 từ]

**Keywords:** keyword1, keyword2, keyword3, keyword4, keyword5

---

## Revision Log

| Version | Date | Changes | Revised By |
|---|---|---|---|
| v1 | dd/mm/yyyy | First draft | Nguyễn Văn A |
| v2 | dd/mm/yyyy | Revised based on feedback | Cả nhóm |
```

---

## 15. Quy định cập nhật Git hằng tuần

Mỗi nhóm phải cập nhật Git ít nhất:

- 2 lần mỗi tuần.
- Mỗi thành viên nên có commit riêng.
- Commit phải có nội dung thật, không commit rỗng.
- File cập nhật phải nằm đúng thư mục.
- Không upload file không liên quan.

### Checklist mỗi tuần

| Tuần | Công việc chính | File cần cập nhật |
|---|---|---|
| Week 1 | Chọn đề tài, phân công, tạo nhánh | `topic_proposal.md`, `task_assignment.md`, `week_01.md` |
| Week 2 | Tìm bài báo liên quan | `paper_list.md`, `search_keywords.md`, `week_02.md` |
| Week 3 | Tóm tắt từng bài báo | `paper_summaries/`, `week_03.md` |
| Week 4 | Literature review matrix | `literature_review_matrix.md`, `week_04.md` |
| Week 5 | Xác định gap và câu hỏi nghiên cứu | `problem_statement.md`, `research_gap.md`, `research_questions.md`, `week_05.md` |
| Week 6 | Viết và hoàn thiện abstract | `abstract.md`, `week_06.md` |

---

## 16. Tiêu chí đánh giá nhóm

| Tiêu chí | Trọng số gợi ý |
|---|---|
| Chất lượng ý tưởng đề tài và phân công | 10% |
| Chất lượng tìm kiếm và danh sách bài báo | 15% |
| Chất lượng tóm tắt từng bài báo | 20% |
| Literature review matrix đầy đủ và có phân tích | 20% |
| Xác định gap và research questions rõ ràng | 20% |
| Chất lượng abstract | 10% |
| Cập nhật Git, báo cáo tuần và làm việc nhóm | 5% |

---

## 17. Checklist trước khi nộp bài cuối

Trước khi nộp, nhóm cần kiểm tra:

- [ ] Tên đề tài rõ ràng, thuộc đúng lĩnh vực định hướng.
- [ ] Có file phân công nhiệm vụ đầy đủ.
- [ ] Có ít nhất 7 bài báo liên quan trong danh sách.
- [ ] Có tóm tắt từng bài báo theo đúng mẫu.
- [ ] Có literature review matrix.
- [ ] Có problem statement.
- [ ] Có research gap.
- [ ] Có research questions.
- [ ] Có abstract tiếng Anh (150-250 từ) với đầy đủ các thành phần.
- [ ] Có keywords.
- [ ] Có 6 báo cáo tuần.
- [ ] Có commit history đầy đủ, mỗi thành viên có commit.

---

## 18. Câu định vị bài báo literature review

Các nhóm có thể sử dụng câu sau để định vị nghiên cứu:

> This study does not aim to propose a new framework or tool. Instead, it conducts a literature review to synthesize existing research on [topic], identify key findings and research gaps, and provide practical insights for [target context].

Phiên bản tiếng Việt:

> Nghiên cứu này không nhằm đề xuất một framework hay công cụ mới, mà thực hiện tổng hợp các nghiên cứu hiện có về [chủ đề], xác định các phát hiện chính và khoảng trống nghiên cứu, đồng thời cung cấp các nhận định có giá trị thực tiễn cho [bối cảnh áp dụng].

---

## 19. Kết luận

Repository này là nơi quản lý toàn bộ quá trình làm bài báo của các nhóm trong 6 tuần.

Mỗi nhóm cần:

- Làm việc trên nhánh riêng.
- Phân công rõ ràng và theo sát tiến độ.
- Cập nhật Git và báo cáo tuần đầy đủ.
- Tìm bài báo có chất lượng từ các nguồn uy tín.
- Tổng hợp và phân tích bài báo có chiều sâu.
- Xác định gap nghiên cứu rõ ràng.
- Hoàn thiện abstract đủ thành phần theo chuẩn học thuật.

Mục tiêu cuối cùng là mỗi nhóm có thể tạo ra một abstract hoàn chỉnh, thể hiện được vấn đề nghiên cứu, phương pháp literature review, các phát hiện chính và đóng góp của bài, làm nền tảng để tiếp tục phát triển thành bài báo đầy đủ trong tương lai.
