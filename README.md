📌 EngageSense AI — Real-Time Student Engagement Detection

EngageSense AI is a rule-based, real-time, and interpretable system that detects student engagement using head pose and eye gaze, built using MediaPipe, Dlib, and OpenCV.
Based on the research project by: Hadi Mostafa & Rein Ghattas.

🎯 Why EngageSense AI?

Traditional engagement detection uses heavy emotion-recognition deep learning models.
But as shown in the research (see Project Article, pg. 1–2 

Project Articale

):

Emotions ≠ attention

Deep models are slow

They require huge datasets

They are NOT interpretable

EngageSense AI solves this by using behavioral cues only:

Eye gaze

Head pose

Rule-based scoring

🧠 System Architecture

As shown in the architecture diagram (pg. 12, presentation) 

Project Presentation

:

Webcam → FaceMesh + Dlib → Rule Engine → Engagement State


Engagement levels:

Engaged (E ≥ 0.7)

Partially Engaged (0.4 ≤ E < 0.7)

Not Engaged (E < 0.4)

Scoring formula (Report pg. 7) 

Project Report

:

E = 0.6 * Gaze + 0.4 * HeadPose

🚀 Features

Real-time (25 FPS CPU-only)

Fully interpretable

Lightweight — NO training

Privacy friendly (no video stored)

PyQt6 dashboard

CSV prediction export

📦 Installation
pip install -r requirements.txt

▶️ Run the application
python app/main.py