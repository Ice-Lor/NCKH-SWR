# Topic Proposal

## 1. Group Information

- **Class:** SE2037
- **Group:** 04
- **Leader:** Nguyễn Hoàng Anh Khoa
- **Members:** Trần Anh Vinh
              Phan Phúc Thịnh
              Nguyễn Thị Quỳnh Trúc
              Nguyễn Quang Trường

---

## 2. Proposed Title

- **English title:** Requirements Engineering for a RAG-based LMS that Generates CLO-aligned Quizzes

---

## 3. Research Domain

- Software Requirements Engineering

---

## 4. Problem Statement

In higher education, especially in software engineering and IT courses, instructors often face repetitive tasks in learning management, such as:

* Creating quizzes and practice questions.
* Providing feedback on student assignments.
* Tracking learning progress.
* Identifying students struggling with specific CLOs (Course Learning Outcomes).
* Recommending appropriate learning materials.
* Supporting students' self-study outside classroom hours.

In traditional LMS (Learning Management Systems), most of these tasks heavily rely on manual efforts by instructors. This leads to several challenges:

* High workload and time consumed in creating learning content.
* Difficulty in personalizing learning for each student.
* Delayed feedback for students.
* Hard to track specific weaknesses of learners.
* Chatbots or support systems often reply generally and lack course context.
* AI-generated content may not align with the syllabus or CLOs.

Meanwhile, Large Language Models (LLMs) and Retrieval-Augmented Generation (RAG) are capable of generating questions, creating learning feedback, magnifying materials, and personalizing content. However, integrating these AI models into an LMS in a course-aware manner and validating its real-world effectiveness remains limited. 

Therefore, this study proposes a requirements engineering framework for a RAG-based LMS that generates CLO-aligned quizzes to save instructors' time and personalize student learning.

---

## 5. Motivation

The rapid development of Generative AI opens up opportunities in higher education. However, current systems have limitations:

* They do not integrate AI directly into the learning workflow.
* Rely on simple chatbots without educational grounding.
* Lack alignment with CLOs or syllabus.
* Do not support personalized learning pathways.
* Do not evaluate AI usefulness and pedagogical impact in real classes.

In Software Engineering courses, the vast content and large student cohorts make it difficult for instructors to generate quizzes regularly, provide detailed feedback, and track learning outcomes. A RAG-based LMS can retrieve course content, generate quizzes per topic, and provide personalized feedback, which helps reduce instructor workload, speed up feedback, and improve student self-study.

---

## 6. Target Users

| User Role | Description |
|---|---|
| Student | Take quizzes, ask questions, view feedback, self-study |
| Instructor | Manage courses, upload materials, generate quizzes, track progress |
| Admin | Manage system and system data |

---

## 7. Proposed AI Model / Method

- LLM & Retrieval-Augmented Generation (RAG)

---

## 8. System Features

### Student Features

* Login and learning management dashboard.
* Take AI-generated quizzes.
* View personalized, explanatory feedback on quiz attempts.
* Chat with AI learning assistant.
* View learning progress and CLO achievements.
* Receive study recommendations.

---

### Instructor Features

* Course management panel.
* Upload course materials (syllabus, slides, textbooks).
* Trigger automated quiz generation.
* Monitor CLO achievement analytics.
* View learning analytics dashboard.
* Manage and override AI-generated feedback.

---

### AI Features

* Quiz generation based on documents.
* Personalized explanatory feedback generation.
* RAG-based learning assistant.
* CLO-aware recommendations.

---

## 9. Expected Contribution

* **A working prototype of a RAG-based LMS** integrating LLMs to help instructors upload learning materials, automatically generate CLO-aligned multiple-choice questions, and allow review/edit.
* **A detailed Software Requirements Specification (SRS)** for educational RAG features.
* **An empirical report** comparing question generation quality between RAG-LMS and a standard LLM-only model.

---

## 10. Evaluation Plan

* **Dataset:** Slides, textbooks, and learning materials of Software Engineering courses (e.g., Software Requirements, Software Architecture).
* **Baseline:**
  1. *Manual:* Traditional manual quiz creation by instructors.
  2. *LLM-only:* Quiz generation directly using LLM without RAG.
* **Metrics:**
  1. *Faithfulness:* Measuring if the generated questions contain hallucinations or ungrounded knowledge.
  2. *Answer Relevance:* Measuring the logical consistency between the question and the correct answer.
  3. *CLO Alignment Rate:* The percentage of questions accurately evaluating the selected CLO.
* **User/Expert Evaluation:** Structured surveys from 2-3 course instructors (Expert Rating) and empirical tests with 15-20 students.

---

## 11. Related Papers

| No | Title | Year | Source | Link / DOI |
|----|-------|------|--------|------------|
| 1 | Exploring the Integration of Virtual Assistant Using Large Language Models in Learning Management System: Enhancing Educational Accessibility and Efficiency | 2024 | IEEE (ICITSI 2024) | 10.1109/ICITSI65188.2024.10929366 |
| 2 | LLM-Based Quiz Generation for Assessments in Learning Management System | 2025 | IEEE (ICC-ROBINS 2025) | 10.1109/ICC-ROBINS64345.2025.11086273 |
| 3 | Enhancing Engineering Education through LLM-Driven Adaptive Quiz Generation: A RAG-Based Approach | 2024 | IEEE (FIE 2024) | 10.1109/FIE61694.2024.10893146 |
| 4 | Generating In-Context, Personalized Feedback for Intelligent Tutors with Large Language Models | 2025 | Springer (Int. Journal of AI in Education) | 10.1007/s40593-025-00505-6 |
| 5 | Retrieval-Augmented Generation for Educational Application: A Systematic Survey | 2025 | Elsevier (Computers and Education: AI) | 10.1016/j.caeai.2025.100417 |