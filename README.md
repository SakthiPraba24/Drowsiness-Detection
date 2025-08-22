# Drowsiness-Detection

Overview

This project detects drowsiness in real-time using a webcam. It tracks the user’s eyes and raises an audio alert when signs of sleepiness (prolonged eye closure) are detected. The system is built with OpenCV, dlib, and pyttsx3 for image processing, facial landmark detection, and audio alerts.

Working

Video Capture

The webcam captures live video using OpenCV.

Face & Eye Detection

dlib’s get_frontal_face_detector() detects faces.

A pretrained model (shape_predictor_68_face_landmarks.dat) maps 68 facial landmarks.

Eye regions are extracted (left eye: points 36–41, right eye: points 42–47).

Eye Aspect Ratio (EAR) Calculation

Uses the Euclidean distance between eye landmarks.

EAR formula:

𝐸
𝐴
𝑅
=
∣
∣
𝑝
2
−
𝑝
6
∣
∣
+
∣
∣
𝑝
3
−
𝑝
5
∣
∣
2
×
∣
∣
𝑝
1
−
𝑝
4
∣
∣
EAR=
2×∣∣p1−p4∣∣
∣∣p2−p6∣∣+∣∣p3−p5∣∣
	​


If EAR < 0.25 (threshold), it means eyes are likely closed.

Alert Mechanism

Displays “DROWSINESS DETECTED” and “You are Sleeping Please Wake up!!” on the screen.

Uses pyttsx3 to speak the warning aloud.

Exit Condition

Program runs until the user presses 'q'.

Key Libraries Used

OpenCV → video capture & drawing on frames.

dlib → face and landmark detection.

scipy → Euclidean distance for EAR.

pyttsx3 → text-to-speech audio alert.
