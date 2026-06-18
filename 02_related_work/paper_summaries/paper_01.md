# Paper 01 Summary

## Citation

- **Title:** KAQG: A Knowledge-Graph-Enhanced RAG for Difficulty-Controlled Question Generation
- **Authors:** Ching Han Chen, Ming Fang Shiu
- **Year:** 2025
- **Source:** arXiv / IEEE TechRxiv
- **Link / DOI:** https://arxiv.org/abs/2505.07618

## Problem

The study addresses the problem of controlling exam question difficulty, psychometric calibration, and cognitive alignment in automated question generation (AQG) systems. Although Large Language Models (LLMs) and conventional RAG frameworks (such as GraphRAG, HippoRAG, LightRAG) improve information accuracy, they lack a systematic mechanism to control cognitive difficulty levels (e.g., according to Bloom's Taxonomy) and psychometric validity (e.g., according to Item Response Theory - IRT), which are crucial for standardized assessment exams.

## Method

The proposed framework, named **KAQG (Knowledge Augmented Question Generation)**, integrates Item Response Theory (IRT), Bloom’s Taxonomy, and Knowledge Graphs (KG) into a distributed multi-agent RAG system. Key features include:
1. **Multi-Graph Isolation:** Each course subject is supported by an independent knowledge graph to eliminate cross-domain terminological noise.
2. **PageRank-based Concept Weighting:** Ranks and selects core learning concepts in the KG using the PageRank algorithm to ensure questions cover the curriculum focus.
3. **IRT 3PL Parameter Calibration:** Maps graph and cognitive attributes to the 3-parameter logistic (3PL) IRT model:
   - Difficulty parameter ($b$): Correlates with graph depth and higher Bloom's cognitive levels (e.g., Analyze, Evaluate).
   - Discrimination parameter ($a$): Correlates with the node degree of concept nodes in the graph.
   - Guessing parameter ($c$): Minimized via multi-hop reasoning on the knowledge graph to generate plausible distractors.
4. **Question Surface Feature Evaluation:** Assesses difficulty based on a combination of 7 MCQ features (stem length, domain vocabulary, cognitive demand, option length, option similarity, stem-option overlap, distractor plausibility) to calculate a generalized difficulty score.
5. **Distributed Multi-Agent Architecture:** Coordinates specialized agents (Retriever, Generator, Evaluator) over Data Distribution Service (DDS) using a publish-subscribe model to improve throughput and fault tolerance.

## Dataset

- The system utilizes a knowledge base built from **102 textbook PDFs** and learning materials.
- For comparative evaluation, the researchers used **3 reading passages from the official ACT Reading exam** (Passage A, B, C) with 10 official questions each as the control group.

## Evaluation

The study uses two complementary evaluation processes:
1. **Human Benchmarking:** Recruited participants divided into 4 groups to take exams consisting of official ACT questions (control) and 3 groups of system-generated questions at Low, Medium, and High difficulty levels. Measured metrics include the correct answer rate (P-value / Difficulty), discrimination index, and expert ratings on question quality (5-point Likert scale).
2. **Simulation Study:** Simulated 5,000 virtual test-takers with ability $\theta_i \sim N(0,1)$. Used the 3PL model to generate response matrices for 90 questions (evenly split across 3 difficulty levels). Applied IRT estimation to compare recovered parameters with the true parameters. Conducted ablation studies on 5 different conditions (Full, -IRT, -Bloom, -IRT&Bloom, Baseline-RAG).

## Results

1. **Human Benchmarking:** The system exhibits stable difficulty control. The Low group has the highest average correct rate ($P = 0.82 \pm 0.06$), the Medium group ($P = 0.71 \pm 0.07$) is similar to the official ACT ($P = 0.76 \pm 0.05$), and the High group has the highest difficulty ($P = 0.63 \pm 0.08$). The discrimination index remains stable ($0.32 - 0.37$), proving the system alters difficulty without losing the ability to distinguish student abilities.
2. **Simulation Study:** The Full model recovers parameters with a very high correlation to the ground-truth for difficulty $b$ (correlation coefficient $0.91$, RMSE $0.22$) and discrimination $a$ ($0.82$). The difficulty misclassification rate is only $6.7\%$, significantly outperforming conditions lacking IRT/Bloom (error rates ranging from $12.5\%$ to $27.8\%$).

## Limitations

- **System Complexity:** Setting up knowledge graphs and the multi-agent system combined with the DDS communication protocol requires substantial computing resources and complex engineering, making it difficult to integrate directly into lightweight LMS platforms.
- **Initial Expert Dependence:** The weights of the 7 surface difficulty features still rely on subjective expert evaluation and have not been fully optimized using large-scale empirical data from real users.
- **Extraction Noise:** Extracting entities and relationships from scanned or blurry PDF textbooks is prone to errors, requiring additional entity normalization post-processing.

## Relevance to our topic

- Confirms the feasibility of integrating educational theories (Bloom's Taxonomy) and psychometrics (IRT) into prompts to control the difficulty of generated questions aligning with Course Learning Outcomes (CLOs).
- Knowledge graphs and the PageRank algorithm provide a solution for filtering and selecting core concepts from lecture slides to generate focused questions, avoiding irrelevant question generation.

## Possible improvement

- **System Simplification:** Remove the complex DDS mechanism and replace it with a sequential RAG workflow integrated directly into the LMS API to optimize response time.
- **Add Explanations for Wrong Answers:** Add a module to automatically generate detailed feedback for incorrect choices (distractor feedback) based on semantic relations in the knowledge graph to support student self-study.
