# Paper 05 Summary

## Citation

- **Title:** Automated Educational Question Generation at Different Bloom's Skill Levels using Large Language Models: Strategies and Evaluation
- **Authors:** Nicy Scaria, Suma Dharani Chenna, Deepak Subramani
- **Year:** 2024
- **Source:** arXiv / Springer (Lecture Notes in Artificial Intelligence, volume 14830)
- **DOI/Link:** https://doi.org/10.1007/978-3-031-64299-9_12 / https://arxiv.org/abs/2408.04394

## Problem

The study focuses on automated educational question generation (AEQG) that aligns with different cognitive levels of Bloom's Taxonomy (from remembering to creating) for large-scale online education. Designing diverse questions that adhere to Bloom's Taxonomy manually requires significant effort from instructors. Most previous AQG systems could only generate questions at lower cognitive levels (recalling facts directly from text) or were limited by the lack of high-quality fine-tuning datasets.

## Method

The study conducts a comparative evaluation of 5 different Large Language Models (LLMs) across 5 prompting strategies (PS) to generate multiple-choice and open-ended questions across 6 Bloom's Taxonomy levels (Remember, Understand, Apply, Analyze, Evaluate, Create) for a graduate-level Data Science course (consisting of 17 topics).
- **5 LLMs tested:** Mistral 7B, Llama 2 70B, Palm 2, GPT-3.5, and GPT-4.
- **5 Prompting Strategies (in order of increasing complexity):**
  - *PS1:* Simple prompt.
  - *PS2:* Chain-of-Thought (CoT) prompt combining detailed definitions of each Bloom's level.
  - *PS3:* CoT prompt combining expert sample questions for each Bloom's level (few-shot).
  - *PS4:* CoT prompt combining both definitions and sample questions.
  - *PS5:* CoT prompt combining definitions, detailed explanations, and sample questions (extremely long prompt).
- **Contextualization:** LLMs were requested to weave in India-related scenarios (Bollywood, agriculture, traffic) to increase engagement.
- **Reference-free Evaluation:** Used Gemini Pro (temperature = 0) to evaluate questions based on the expert rubric. Measured question diversity using the PINC score.

## Dataset

The self-built dataset is named **DataScienceQ**, containing **2,550 questions** generated from the combination of 5 LLMs, 5 prompting strategies, across 17 Data Science topics (such as Linear Regression, Prompt Engineering, etc.).

## Evaluation

Question quality was evaluated via:
1. **Human Evaluation (Expert Assessment):** 2 Data Science instructors graded random questions based on a 9-item Hierarchical Rubric (Understandable, TopicRelated, Grammatical, Clear, Rephrase, Answerable, Central, WouldYouUseIt, Bloom'sLevel). The evaluation featured an early stopping mechanism if questions failed basic criteria (like understandability). Measured Cohen's Kappa and Quadratic Weighted Kappa to evaluate rater agreement.
2. **LLM Evaluation:** Gemini Pro graded questions using the same rubric to compare its correlation with human experts.

## Results

1. **Question Quality & Bloom Adherence:** **78% of generated questions** were rated as High Quality by experts, and **65.56% of questions** mapped accurately to the requested Bloom's level. The average PINC diversity score was 0.92, showing that the generated questions were diverse in phrasing and did not have repetitive patterns.
2. **Model Performance:** GPT-4 and GPT-3.5 led the test (GPT-4 achieved 89.02% high quality, GPT-3.5 achieved 86.27%). There was no clear linear correlation between model size and quality (e.g., Mistral 7B performed better than Llama 2 70B in several complex prompts).
3. **Prompt Strategy Impact:** Question quality increased progressively from PS1 to PS4. **PS4 (CoT + Bloom definitions + sample questions)** provided the optimal results across all models. However, extremely long prompts like **PS5 backfired**, causing quality and Bloom compliance in smaller models (Mistral, Llama 2, Palm 2) to drop sharply (average Bloom compliance decreased from 72% to 51%).
4. **LLM Evaluation:** Gemini Pro's ratings correlated poorly with human experts, proving that current LLMs are not yet reliable enough to automatically grade educational question quality.

## Limitations

- **Lack of RAG:** The study relied entirely on the internal knowledge of LLMs without providing external context documents, posing a high risk of hallucination when applied to domain-specific or newly emerged topics.
- **Poor Local Language Accuracy:** Open-source models (Mistral, Llama 2) generated localized Indian language texts with severe grammatical and translation errors.

## Relevance to our topic

- Proves the feasibility of guiding LLMs to generate questions aligned with Bloom's Taxonomy cognitive levels to meet Course Learning Outcomes (CLOs).
- Offers a practical lesson on prompt design: directly apply the PS4 prompting strategy (CoT + Bloom/CLO explanation + few-shot examples) to the LMS quiz generation system.
- Inherits a highly scientific 9-item hierarchical rubric and an early stopping mechanism to optimize the instructor's question quality evaluation process.

## Possible improvement

- **Integrate RAG:** Combine RAG on course slides with the PS4 prompt strategy to ensure questions are both cognitively aligned and factually accurate according to classroom lectures, eliminating hallucinations.
- **Automated Feedback Generation:** Expand the system to generate corrective feedback (explanation of incorrect choices) based on the corresponding Bloom's cognitive levels.
