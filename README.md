
# EngageSense AI

## A Rule-Based System for Real-Time Student Engagement Detection Using Head Pose and Eye Gaze

EngageSense AI is a lightweight, fully interpretable, rule-based computer vision system designed to detect real-time student engagement in online learning environments using behavioral cues only.

Unlike emotion-driven deep learning systems, EngageSense AI relies exclusively on head pose and eye gaze geometry to infer attentional engagement. The system operates in real time on CPU-only hardware and achieves 82.2% classification accuracy without requiring model training or GPU acceleration .

---

# Table of Contents

1. Overview
2. Motivation
3. Research Contribution
4. System Architecture
5. Engagement Scoring Model
6. Dataset and Evaluation
7. Results
8. Technical Stack
9. Installation
10. Usage
11. Project Structure
12. Ethical Considerations
13. Limitations
14. Future Work
15. Citation

---

# 1. Overview

EngageSense AI detects student engagement in real time by analyzing:

* Eye gaze direction
* Head pose orientation

The system classifies engagement into three categories:

* Engaged
* Partially Engaged
* Not Engaged

The model is deterministic and fully rule-based, ensuring complete interpretability and transparency .

---

# 2. Motivation

Online learning environments make it difficult for instructors to observe traditional engagement indicators such as:

* Eye contact
* Posture
* Attentiveness

Existing AI solutions typically rely on:

* Emotion recognition
* Deep neural networks
* Large labeled datasets (e.g., DAiSEE, AffectNet)

However, emotional expressions do not necessarily reflect attentional focus, and deep learning systems:

* Require large datasets
* Depend on GPU acceleration
* Act as black-box models
* Lack transparency

EngageSense AI addresses this gap by using purely behavioral, interpretable rules for engagement detection .

---

# 3. Research Contribution

EngageSense AI provides:

* A fully rule-based engagement detection system
* No training or pretraining required
* Real-time operation at approximately 25 FPS on CPU hardware
* Transparent decision logic
* Competitive performance (82.2% accuracy)

This project demonstrates that behavioral cues alone are sufficient for reliable engagement detection in educational contexts .

---

# 4. System Architecture

The system consists of four main modules:

1. Webcam Frame Capture (OpenCV)
2. Feature Extraction (MediaPipe FaceMesh + Dlib)
3. Rule-Based Inference Engine
4. Output Visualization

According to the system diagram in the methodology report (Figure 1, page 8) , the pipeline follows:

Webcam → Landmark Extraction → Gaze & Head Pose Estimation → Rule-Based Scoring → Engagement Classification → Visualization

---

# 5. Engagement Scoring Model

The engagement score is computed using a weighted combination of gaze and head pose:

[
E = 0.6G + 0.4H
]

Where:

* G = Gaze value ∈ {1, 0.5, 0}
* H = Head pose value ∈ {1, 0.5, 0}

Gaze receives a higher weight because it correlates more strongly with attentional focus .

### State Definitions

**Gaze / Head Pose States:**

* 1 → Fully aligned with screen
* 0.5 → Slight deviation
* 0 → Looking away

### Classification Thresholds

* Engaged → E ≥ 0.7
* Partially Engaged → 0.4 ≤ E < 0.7
* Not Engaged → E < 0.4

This rule-based design ensures complete interpretability and traceability of predictions .

---

# 6. Dataset and Evaluation

A manually annotated dataset of approximately 1,000 frames was created for evaluation .

Each frame was labeled into:

* Engaged
* Partially Engaged
* Not Engaged

### Evaluation Metrics

The following metrics were computed:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix

Metric definitions are formally presented in Table 2 of the methodology report (page 8) .

---

# 7. Results

The system achieved:

* Overall Accuracy: 82.2%
* Real-Time Speed: ~25 FPS (CPU only)

### Performance by Class

| Class             | Precision | Recall | F1-score |
| ----------------- | --------- | ------ | -------- |
| Engaged           | 0.819     | 0.844  | 0.831    |
| Partially Engaged | 0.834     | 0.832  | 0.833    |
| Not Engaged       | 0.812     | 0.790  | 0.801    |

(Metrics reported in Chapter 4, Results section) .

The confusion matrix (Figure 2, page 9) shows that most misclassifications occur between Engaged and Partially Engaged, which is expected due to subtle boundary transitions .

---

# 8. Technical Stack

* Python 3.x
* OpenCV (real-time frame capture)
* MediaPipe FaceMesh (eye landmark extraction)
* Dlib (68-point facial landmark model for head pose)
* NumPy
* Scikit-learn (evaluation metrics)

---

# 9. Installation

```bash
git clone https://github.com/yourusername/EngageSense-AI.git
cd EngageSense-AI
pip install -r requirements.txt
```

Ensure that:

* A working webcam is connected
* Python 3.8+ is installed

---

# 10. Usage

```bash
python main.py
```

The system will:

1. Activate webcam capture
2. Extract gaze and head pose features
3. Compute engagement score
4. Display real-time engagement state

---

# 11. Project Structure

```
EngageSense-AI/
│
├── main.py
├── capture.py
├── feature_extraction.py
├── scoring_model.py
├── evaluation.py
├── utils/
├── dataset/
├── results/
└── README.md
```

---

# 12. Ethical Considerations

EngageSense AI was designed with strict privacy preservation principles:

* No raw video frames are stored
* Only numerical behavioral features are retained
* No identifiable facial images are saved
* Fully compliant with classroom ethical standards

As described in the methodology (Chapter 3, page 8) .

---

# 13. Limitations

* Dataset size is limited (~1,000 frames)
* Initial evaluation included limited participant diversity
* Only behavioral cues used (no posture, blinking, or multimodal signals)

Generalizability may improve with larger, multi-user datasets .

---

# 14. Future Work

Planned improvements include:

* Expanding dataset across multiple users
* Multi-student detection in a single frame
* Integration with Learning Management Systems
* Hybrid rule-based + lightweight ML models
* Additional behavioral cues (posture, blink rate)

Outlined in Chapter 6 of the research report .

---

# 15. Citation

If you use this work, please cite:

Mostafa, H., & Ghattas, R.
"EngageSense AI: A Rule-Based System for Real-Time Student Engagement Detection Using Head Pose and Eye Gaze."
Beirut Arab University, 2025-2026. 

