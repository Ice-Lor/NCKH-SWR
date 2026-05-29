# Paper 01 Summary 

## Citation

*   **Title:** Technologies for sleep monitoring at home: wearables and nearables
*   **Authors:** Heenam Yoon & Sang Ho Choi
*   **Year:** 2023
*   **Source:** Biomedical Engineering Letters (Volume 13, Issue 3, pp. 313–327)
*   **DOI/Link:** https://doi.org/10.1007/s13534-023-00305-8 (PMCID: PMC10382403)

---

## Problem

The paper addresses the critical bottleneck of transitioning sleep medicine from clinical environments to long-term home monitoring. 

### The Core Conflict
The clinical gold standard for sleep staging is **Polysomnography (PSG)**, which records a comprehensive suite of physiological signals (EEG, EOG, EMG, ECG, and respiratory effort). While highly accurate, PSG is extremely obtrusive, expensive, and limits longitudinal (night-by-night) sleep tracking.

### The Technical Challenge for Consumer Technologies
To replace PSG at home, market alternatives like smartwatches and bedside radars have emerged. However, these systems face a severe engineering challenge: **the inability to accurately distinguish between quiet wakefulness (lying completely still in bed while awake) and actual sleep.** 
*   **Actigraphy-only systems** rely purely on motion. When a user is in a state of "inactive awake time" (e.g., scrolling phone, reading, or meditating in the dark), motion drops to zero. 
*   Without multi-modal sensors, standard algorithms misclassify this entire period as sleep, severely overestimating **Sleep Efficiency (SE)** and underestimating **Sleep Onset Latency (SOL)**.

---

## Method

The authors synthesize the technical architectures of home monitoring by splitting them into two macro-domains, mapping out their underlying hardware and signal processing pipelines:

### 1. Wearables Architectural Pipeline
*   **Sensing Layer:** Uses **3-axis Accelerometers** to capture raw acceleration ($g$-force) and **Photoplethysmography (PPG)** sensors using green/red/infrared LEDs to measure changes in blood volume.
*   **Feature Extraction Layer:** 
    *   *Motion:* Traces movement counts, zero-crossing rates, and signal magnitude areas.
    *   *Autonomic Nervous System (ANS):* Traces **Heart Rate Variability (HRV)** features in both Time-Domain (SDNN, rMSSD) and Frequency-Domain (Low Frequency/High Frequency ratio - LF/HF).
*   **Classification Layer:** Employs advanced deep networks like **Bidirectional Long Short-Term Memory (BiLSTM)** and **Convolutional Neural Networks (CNNs)** to classify 3-stage (Wake, NREM, REM) or 4-stage (Wake, Light, Deep, REM) sleep.

### 2. Nearables Architectural Pipeline
*   **Radio Frequency (RF) / Radar Systems:** Uses **Impulse Radio Ultra-Wideband (IR-UWB)** and **Continuous Wave (CW) Doppler** radars to isolate sub-millimeter chest wall displacements caused by respiration (0.1–0.5 Hz) and heartbeats (1.0–3.0 Hz).
*   **Ballistocardiography (BCG):** Piezoelectric or polyvinylidene fluoride (PVDF) film sensors embedded inside mattresses or pillows to measure the mechanical recoil forces of the body caused by blood ejection.
*   **Acoustic Sensing:** Microphones recording room audio, passing signals through Bandpass Filters (200 Hz – 2000 Hz) to extract acoustic signatures of snoring and breathing.

---

## Dataset

The paper reviews outcomes validated against two primary data paradigms:

1.  **Clinical/Benchmark Datasets (Ground Truth Control):**
    *   **PhysioNet / Sleep Heart Health Study (SHHS):** Public repositories containing full-channel PSG data used to train deep learning networks.
    *   **Multi-Center Clinical Cohorts:** Studies where patients wore consumer devices (e.g., Apple Watch, Fitbit, Oura Ring) *simultaneously* while undergoing clinical PSG tests in hospital sleep units.
2.  **In-The-Wild Consumer Datasets:**
    *   Large-scale unlabelled datasets collected from commercial cloud servers to showcase real-world noise, such as device removal mid-night, battery depletion events, and erratic sleep schedules.

---

## Evaluation

The paper details how home sleep technologies are benchmarked using a rigorous dual-layer metric framework:

### 1. Statistical Classification Metrics
Algorithms are evaluated by constructing a confusion matrix against PSG epoch-by-epoch (30-second windows) scoring:
*   **Overall Accuracy (ACC):** The percentage of correctly identified epochs across all stages.
*   **Sensitivity (True Positive Rate) for Wake vs. Sleep:** Specifically tracking how well the system detects the Wake state.
*   **Cohen’s Kappa Coefficient ($\kappa$):** Measures inter-rater agreement between the AI model and the human expert score, adjusting for chance:

$$\kappa = \frac{p_o - p_e}{1 - p_e}$$

### 2. Clinical Sleep Parameters (Epoch Aggregations)
*   **Total Sleep Time (TST):** Total minutes classified as sleep.
*   **Sleep Onset Latency (SOL):** The time taken to transition from full wakefulness to the first epoch of sleep.
*   **Wake After Sleep Onset (WASO):** Total minutes spent awake after initially falling asleep.
*   **Sleep Efficiency (SE):** Calculated as:

$$SE = \left( \frac{TST}{\text{Total Time in Bed}} \right) \times 100\%$$

---

## Results

*   **The Power of Wearable Multi-Modal Fusion:** Systems using *only* Accelerometers achieve poor accuracy in sleep staging (ACC ~ 65-70%) and fail during inactive wake times. However, when **Accelerometry is fused with PPG (HRV features)**, deep learning models achieve an ACC of **78% to 86%** and a Kappa ($\kappa$) of **0.55 to 0.72**.
*   **Nearable Radar Precision:** Non-contact IR-UWB radar systems demonstrate exceptional capabilities in tracking breathing patterns, allowing them to detect **Sleep Apnea (Apnea-Hypopnea Index - AHI)** with a correlation coefficient of $r > 0.85$ compared to PSG.
*   **The Inactive Wake Breakthrough:** The combination of autonomic nervous system tracking (via PPG) and macro-motion tracking (via Actigraphy) allows systems to detect the **Sympathetic Hyperarousal** characteristic of wakefulness. Even when a person lies perfectly still, their heart rate variability exhibits an elevated LF/HF ratio, exposing the fact that they are awake.

---

## Limitations

*   **The Multi-Occupancy Failure Mode (Nearable Vulnerability):** Bedside radars and microphones cannot isolate signals effectively if two people share the same bed due to overlapping radar reflections.
*   **Motion Artifacts (Wearable Vulnerability):** Voluntary movements like tossing and turning create massive high-amplitude noise in PPG sensors, leading to corrupted optical readings and missing data data.
*   **Lack of Demographic Diversity:** Most algorithmic models reviewed were trained on specific clinical populations or young, healthy cohorts, often failing when deployed on demographics with irregular sleep architecture.

---

## Relevance to our topic

This paper serves as the primary **Architectural Blueprint** for your project:

### 1. Direct Solution
The paper proves that a single device cannot solve the "inactive awake time" problem reliably. To distinguish inactive awake time from sleep, your system must mandate **Multi-Device Multi-Sensor Fusion**. 
*   If Device A (Wrist-worn Accelerometer) reports `Motion = 0`, the system must not immediately infer `Status = Sleep`. 
*   It must analyze Wearable PPG data. If `HRV = Sympathetic Dominance (High LF/HF Ratio)`, the system overrides the motion sensor and correctly flags the epoch as `Inactive Awake Time`.

### 2. Engineering Functional Requirements (FR)
You can directly derive your software's functional requirements from the sensor pipelines reviewed in the paper:
*   *FR-1:* The system shall ingest data streams concurrently from a wearable unit (PPG, 3-axis Accelerometer) and a nearable environment unit.
*   *FR-2:* The system shall execute a time-synchronization protocol to align epoch timestamps ($T_{\text{epoch}} = 30s$) across all connected devices with a maximum clock drift of $\le 100\text{ms}$.

---

## Possible improvement (Novelty for Your Project)

Your team can build upon this review paper by engineering concrete solutions to the gaps it identifies, turning them into your research's core contributions:

### 1. Formulating a "Multi-Device Failover and Trust Hierarchy"
The review paper lists the pros and cons of devices but doesn't provide a software architecture for when one device fails. Your team can design a **Dynamic Trust-Weighted State Machine** for your requirements specification:
*   *Scenario:* If high motion noise is detected on the Wearable, the system automatically decreases Wearable PPG trust weight and increases Bedside Radar trust weight for sleep staging.

### 2. Designing Requirements for the "Student Screen-Time Context"
Since your target demographic includes students, you can introduce a third, unconventional monitoring device: **The Smartphone Screen-State/Application Log**. 
*   Students frequently lie completely still in bed while scrolling through social media (inactive awake time). 
*   By adding a functional requirement to track **Smartphone Interaction Events** (Screen On/Off states, touch telemetry) and fusing this with the wearable's accelerometer data, your system can achieve high classification accuracy for this specific user group without needing expensive medical-grade radar sensors.