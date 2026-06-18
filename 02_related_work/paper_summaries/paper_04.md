# Paper 04 Summary

## Citation

- **Title:** Generating In-Context, Personalized Feedback for Intelligent Tutors with Large Language Models
- **Authors:** Jennifer M. Reddig, Arav Arora, Christopher J. MacLellan
- **Year:** 2025
- **Source:** International Journal of Artificial Intelligence in Education (Springer)
- **DOI/Link:** https://doi.org/10.1007/s40593-025-00505-6

## Problem

The study focuses on generating personalized corrective feedback in Intelligent Tutoring Systems (ITS). To effectively improve learning outcomes, feedback must be tailored to the specific errors made by students. However, establishing bug rules manually is highly time-consuming, expensive, and inflexible when dealing with unexpected student behavior. Relying solely on raw LLMs to solve problems and directly generate feedback is prone to hallucinations and misleading instructions.

## Method

The research team proposes integrating an LLM (specifically GPT-4) into the **Apprentice Tutors** ITS platform to automate error diagnosis and feedback generation:
1. **Inductive Error Classification:** Analyzes student error data and categorizes them into 5 groups:
   - *Logical Mistake:* Applying wrong rules or incorrect calculations.
   - *Syntax Error:* Typing errors, incorrect formatting.
   - *Incomplete:* Exiting the input field before completing the response.
   - *Wrong Field:* Entering the correct answer of another step into the current field.
   - *Correct Answer:* Correct response marked as incorrect due to accumulated errors from previous steps.
2. **Diagnosis & Feedback Prompting:** Uses Chain-of-Thought (CoT) prompting to provide GPT-4 with ITS context: student input, expected answer, tutor UI, target skill, and Bayesian Knowledge Tracing (BKT) estimates. GPT-4 is instructed to describe the error first before writing the corrective hint.
3. **Automated Evaluation via Simulated Student:** Employs an LLM acting as a virtual student to interact with the system based on the generated hints, measuring if students can self-correct and reach the correct answer.

## Dataset

- Uses real-world student data collected from a College Algebra class during the Spring 2024 semester on the Apprentice Tutors system.
- Total transactions recorded: **6,926 learning transactions**.
- Erroneous transactions used for feedback generation: **1,307 incorrect responses**.

## Evaluation

The study evaluates the system through three research questions (RQs):
1. **Error Diagnosis Accuracy:** Compares GPT-4's automated error diagnosis against manual analysis from 2 experts (measuring accuracy and Cohen's Kappa, achieving 0.931).
2. **Human Evaluation of Feedback Quality:** Educational experts visually evaluated the generated hints for relevance, detail, and pedagogical value.
3. **Automated Evaluation of Feedback Quality:** Measured the pass rate of simulated students who could successfully solve the problem after receiving the LLM-generated hint.

## Results

1. **Error Diagnosis:** GPT-4 diagnosed student errors with **approximately 80% accuracy** for single errors. Accuracy dropped significantly when student answers contained multiple complex errors (>1 error).
2. **Corrective Feedback Quality:** The majority of generated hints showed good personalization. However, **35% of hints were rated as erroneous** because they were too general, explained concepts incorrectly, or directly revealed the correct answer (bottom-out hint), defeating the pedagogical purpose of self-study.
3. **Simulated Student Effectiveness:** Only **35% of the feedback passed** the automated simulated student usefulness test. This indicates that using LLMs to automatically evaluate feedback quality still has major limitations and cannot fully replace human review.

## Limitations

- **Highly Structured Subject:** The experiments were conducted only on College Algebra, a subject with extremely strict logical structures and abundant training data in LLMs, making it difficult to generalize to theoretical or soft-skill subjects.
- **High Error Rate in Feedback:** An error rate of 35% in generated hints or answer leaks is too high for a fully automated real-world educational deployment.
- **Lack of RAG:** The system relies entirely on zero-shot/few-shot prompts without integrating RAG to retrieve background knowledge from course materials for generating highly accurate explanations.

## Relevance to our topic

- Provides a student error classification model (specifically distinguishing logical mistakes, syntax errors, and wrong field entries) to design the error diagnosis logic in our LMS.
- Indicates that to deploy the system in real-world classes, it is mandatory to have feedback quality control or integrate a teacher review panel (Human-in-the-loop) to filter out the 35% erroneous responses.

## Possible improvement

- **RAG-based Feedback Generation:** Integrate RAG to retrieve formulas, definitions, or specific lecture slides related to the student's error. This allows the LLM to generate 100% accurate feedback grounded in classroom materials, eliminating vague or incorrect feedback.
- **Prompt Optimization:** Apply Socratic Mentor prompting to guide students to identify their errors instead of giving them the correct answer directly.
