# Paper 02 Summary

## Citation

* **Title:** Developing a Data Trust Model (Not Only) for Sleep Research: Conceptual Study and Quantitative Survey
* **Authors:** Raphael Jan Dressle, Dieter Riemann, Nicole Thoma, Christina Erler, Rodger Burmeister, Bianka Jogwitz, Katharina Domschke, Kai Spiegelhalder, Joachim Boldt, Svenja Wiertz, Bernd Feige
* **Year:** 2025
* **Source:** JMIR Human Factors (Volume 12, e66513)
* **DOI/Link:** https://doi.org/10.2196/66513

---

## Problem

The paper addresses a critical legal, ethical, and organizational bottleneck in digital health informatics: the low availability and high fragmentation of medical health data for secondary research use.

### The Core Conflict
While healthcare platforms generate massive streams of sensitive physiological and tracking data (such as continuous polysomnography or wearable signals), this data remains locked in institutional silos. The strict enforcement of privacy laws like the European GDPR classifies even pseudonymized healthcare keys as personal identifiable data, explicitly preventing easy data reuse without strict legal bases.

### The Human and Process Challenge
To safely unlock this data, platforms must balance three conflicting stakeholder vectors:
1. Data Subjects (Patients/Users): Willing to share data but demand ultimate transparency, absolute data security, and an active say in who uses their bedroom or physiological data.
2. Data Users (Researchers): Require standardized formats, dense metadata structures, and scalable querying tools without heavy bureaucratic friction.
3. Data Generating Institutions (Clinics/Centers): Require ironclad compliance verification to satisfy legal liabilities and maintain patient care duties.

---

## Method

The authors engineered and evaluated a comprehensive data trust framework called SouveMed, specifically tailored for medical data secondary usage in sleep research. The methodology was executed in a 5-step participatory lifecycle:

### 1. Requirements Elicitation
Conducted initial surveys and workshops involving 14 foundational participants (10 data subjects, 4 data users) to outline baseline functional parameters.

### 2. Multi-Tiered Structural Design
The technical framework separated the onboarding process from the active consent act, implementing a Tiered Consent Model. Users can dynamically adjust data access privileges over time via a digital web interface.

### 3. Automated Contract Matching Architecture
At the system's core, the authors built a neutral data-trust matching server. It automatically parses the legal requirements of the clinic, the permission levels of the user, and the data request queries of the researcher using constraint-solving mechanics to execute zero-human-intervention authorization.

### 4. Interactive Prototype Validation (Two Evaluation Rounds)
* Round 1 Evaluation: Testing static interface mock-ups with an active cohort to capture primary behavioral friction.
* Round 2 Evaluation: Deploying a refined functional web application prototype incorporating programmatic algorithms under a controlled execution sandbox ("curious containers") to preserve user privacy.

---

## Dataset

The empirical datasets compiled and utilized during this human-factors evaluation consist of:
* Psychometric and Evaluation Survey Data: Gathered across sequential testing groups comprising 22 active evaluators in Round 1 (11 sleep patients, 11 professional researchers) and 16 active evaluators in Round 2 (10 sleep patients, 6 research data users).
* Demographic Profile Stratification: Tracks historical data sharing willingness, baseline technical and app literacy, age distributions (ranging from 18 to 75 years), and general stakeholder expectations.

---

## Evaluation

The programmatic usability and psychosocial acceptance of the SouveMed data trust prototype were quantified through three core measurement batteries:

### 1. Human-Computer Trust Scale (HCTS)
A 12-item metrics instrument assessing user trust mapped directly into three essential dimensions:
* Benevolence: The user's systemic belief that the platform prioritizes their personal health privacy interests.
* Competence: Verification that the technical architecture accurately handles and filters complex constraints.
* Perceived Risk: The quantitative probability score assigned by users regarding potential data leaks or privacy harms.

### 2. User Version of the Mobile Application Rating Scale (uMARS)
Quantifies application frontend and software quality across standardized fields evaluated on a 5-point scale:
* Functionality: Evaluating navigation clarity, step-by-step logic, and interface learnability.
* Aesthetics: Gauging the raw visual appeal and layout layout distribution.

### 3. Quantitative Statistical Verification
Mean group score deltas between Evaluation Round 1 and Evaluation Round 2 were analytically calculated via Independent-samples Welch t-tests to prove usability enhancements, calculating Hedges' g for precise effect sizing.

---

## Results

* **Sustained Structural Trust:** Across both deployment cycles, data subjects maintained an exceptional, unchanging baseline trust score in the data trust concept, showing a high mean rating in both evaluation rounds.
* **Significant Usability Progression:** The refinement of the web interface led to a massive, statistically significant jump in the researcher-facing system's Functionality score. It surged from Round 1 up to Round 2 with a remarkably large effect size.
* **High Institutional Feasibility:** When presented with the decentralized data trust model, 100% of institutional data protection officers and medical representatives formally agreed to the conceptual adoption of SouveMed within their live infrastructure workflows.
* **The User Engagement Requirement:** 60% of data subjects declared it vital to receive continuous project descriptions, and 50% demanded active feedback channels detailing the clinical findings derived specifically from their shared data.

---

## Limitations

* Sample Scale Constraints: The quantitative evaluation relied on a small pool of trial subjects (22 and 16 participants across successive iterations), limiting broad statistical generalizability.
* Demographic Selection Bias: The testing population was drawn exclusively from a single clinical university sleep laboratory context, meaning participants possessed higher-than-average technical or clinical literacy.
* Short-Term Interaction Window: The survey tracks prompt, immediate perceptions of usability and trust during controlled testing, leaving long-term compliance behaviors or consent fatigue unmeasured.

---

## Relevance to our topic

This paper serves as the explicit operational foundation for your project's RQ1 (User Requirements) and RQ3 (Validation):

### 1. Concrete Blueprint for RQ1 (Privacy & User Control Specification)
The paper proves that users reject "all-or-nothing" privacy approaches. To build high user adoption among students, your Software Requirements Specification (SRS) must feature the exact core mechanism validated in SouveMed: Tiered Data Control. Your functional architecture should explicitly separate the user onboarding stage from the granular permission state machine, allowing students to turn off specific bedroom telemetry logs while continuing to trust the primary application ecosystem.

### 2. Methodological Playbook for RQ3 (Empirical Prototype Verification)
You can directly replicate SouveMed's validation pipeline for your project's evaluation phase. Instead of presenting a generic UI, your evaluation methodology can deploy a similar two-stage validation loop. You can utilize their exact standardized uMARS and HCTS metric variables to statistically prove to your project evaluation board that your multi-device conflict resolution interface directly minimizes user confusion and mathematically builds long-term user trust.

---

## Possible improvement (Novelty for Your Project)

Your system can advance beyond the SouveMed framework by introducing the following engineering innovations:

### 1. Requirements for Dynamic Multi-Device Conflict Explanations
SouveMed focuses on automated constraint matching based on legal terms but does not explain algorithmic discrepancy to the user. Your project can pioneer Contextual Explanation Requirements. When your system runs its matching layers and detects a data conflict (for example, a student's watch records zero motion but their phone logs active application use), the system should generate a clear, transparent notification rather than just hiding the conflict. You can empirically test if this cross-device explanation pattern increases the Human-Computer Trust score.

### 2. Automating Consent Triggers Based on Academic Deadlines
While SouveMed utilizes a static time-based archive for consent validity, your target domain allows for Context-Aware Dynamic Privacy Policies. You can specify software requirements where the data trust system automatically scales its data collection up or down depending on the student's academic cycle (such as requesting tighter multi-device tracking during exam weeks to detect sleep depreciation, while reverting to absolute minimal tracking during holiday breaks), optimizing the trade-off between tracking accuracy and data exposure.