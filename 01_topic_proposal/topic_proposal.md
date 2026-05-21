# Topic Proposal

## 1. Group Information

- Class: SE2037
- Group: G01
- Leader: Văng Khánh Khuyên
- Members: Văng Khánh Khuyên, Võ Gia Huy, Nguyễn Văn Quốc Bảo, Võ Nguyễn Thiên Phú, Đỗ Thanh Triết

## 2. Proposed Title

English title: 
> Multi-Device Behavioral Data Fusion Using XGBoost for Accurate Distinction Between Inactive Awake and Actual Sleep

Vietnamese title: 
>Hợp nhất dữ liệu hành vi đa thiết bị sử dụng XGBoost để phân biệt chính xác giữa trạng thái “Thức nhưng không sử dụng thiết bị” và “Ngủ thực sự”


## 3. Application Domain

Healthcare

## 4. Problem Statement

Most existing sleep tracking applications primarily rely on data from a single device, typically a smartphone, which leads to frequent misclassification between two distinct states: “Inactive Awake” (the user is awake but not interacting with the device) and “Actual Sleep”. This issue commonly occurs when users switch to working on a laptop, reading on a Kindle, or simply put their phone aside while remaining awake.

As a result, these applications often overestimate sleep duration, reducing the reliability and usefulness of sleep monitoring. Although some studies have explored multi-device approaches, there is still limited research on effectively fusing detailed behavioral data from both smartphones and laptops to accurately distinguish between these two states in real-world scenarios.

## 5. Motivation

In today’s digital lifestyle, young adults and office workers frequently switch between smartphones and laptops, making accurate sleep tracking increasingly challenging. Current applications often fail to differentiate between putting devices aside while still awake and actually falling asleep, leading to poor sleep monitoring quality.

This research aims to address this gap by developing a multi-device behavioral data fusion model using XGBoost to improve the distinction between “Inactive Awake” and “Actual Sleep”. XGBoost is selected for its strong performance on tabular data, efficiency on student-level hardware, and good interpretability, contributing to a practical AI solution for digital health applications.

## 6. Target Users

The primary target users of this research are young adults and office workers aged 18–35 who frequently use multiple digital devices (smartphones and laptops) in their daily lives. These users often switch between devices for work, entertainment, and study until late at night.

## 7. Proposed AI Model / Method

#### Model: 
> XGBoost (eXtreme Gradient Boosting)
#### Method:
 A Multi-Device Behavioral Data Fusion approach using XGBoost as the main classifier. The system extracts rich behavioral features from both smartphones and laptops, then fuses them into a unified feature vector for training and inference.

## 8. System Features

#### 1. Multi-Device Data Collection
- Collect behavioral data from both smartphone and laptop in real-time.
- Support cross-device user identification via account synchronization.

#### 2. Behavioral Feature Extraction
- Smartphone: screen status, touch events, scrolling, typing, app usage, motion (accelerometer), idle duration.
- Laptop: mouse movement, keyboard activity, foreground applications, system idle time, etc.

#### 3. Sleep State Classification
- Real-time / near real-time classification: Inactive Awake vs Actual Sleep.
- Optional: Sleep duration estimation.

#### 4. Dashboard & Visualization
- Daily sleep report with sleep start/end time.
- Device usage patterns before sleep.
- Accuracy feedback and manual correction (user feedback loop).

## 9. Expected Contribution

- Develop a multi-device system that uses behavioral data from both smartphone and laptop to better distinguish between “Inactive Awake” and “Actual Sleep” states.
- Show that XGBoost can work well for this sleep detection task when combining data from multiple devices.
- Build a lightweight AI model that is suitable for students and can be used in a real MVP application.
- Collect and provide a small multi-device behavioral dataset (phone + laptop) for future research.
- Give practical experience and guidelines on building multi-device AI systems for sleep tracking.

## 10. Evaluation Plan

#### 1. Dataset

- Collect real data from 10 - 15 students (including the team members themselves).
- Each participant will use the system for 5–7 days.
- Labeling will be done using a simple sleep diary — participants manually record their actual sleep and wake-up times.
- Data split: 70% for training, 30% for testing.

#### 2. Baseline Models

- Single-device model (using only smartphone data).
- Rule-based model (based on idle time threshold).

#### 3. Evaluation Metrics

- Accuracy
- Precision
- Recall
- F1-Score
- Sleep onset time error (in minutes)
- Sleep duration estimation error

#### 4. User Testing & Survey

- Participants will test the system and complete a short survey about: Perceived accuracy of the system, ease of use, somparison with existing sleep tracking apps.

- Conduct short interviews with some users to gather feedback and improvement suggestions.

## 11. Related Papers

Liệt kê ít nhất 5 bài báo liên quan.

| No | Title | Year | Source | Link / DOI |
|---|---|---|---|---|
| 1 | Toss 'n' turn: smartphone as sleep and sleep quality detector | 2013 | CHI | https://dl.acm.org/doi/pdf/10.1145/2556288.2557220 |
| 2 | Sleep quality prediction from wearable data using deep learning | 2016 | JMIR mHealth and uHealth | https://mhealth.jmir.org/2016/4/e125/ |
| 3 | SensibleSleep: A Bayesian Model for Learning Sleep Patterns from Smartphone Events | 2017 | PLoS ONE | https://journals.plos.org/plosone/article/file?id=10.1371/journal.pone.0169901&type=printable |
| 4 | Unobtrusive sleep monitoring using smartphones | 2013 | PervasiveHealth | https://pac.cs.cornell.edu/pubs/Unobtrusive_Sleep_2013.pdf |
| 5 | Towards Circadian Computing: "Early to Bed and Early to Rise" Makes Some of Us Unhealthy and Sleep Deprived | 2014 | ACM UbiComp | https://dl.acm.org/doi/pdf/10.1145/2632048.2632100 |
