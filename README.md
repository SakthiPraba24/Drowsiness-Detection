# Drowsiness-Detection

### Overview

This project detects drowsiness in real-time using a webcam. It tracks the user’s eyes and raises an audio alert when signs of sleepiness (prolonged eye closure) are detected. The system is built with OpenCV, dlib, and pyttsx3 for image processing, facial landmark detection, and audio alerts.

### Download model file
This project requires the pretrained dlib 68 face landmarks model.

Download the file by searching **shape_predictor_68_face_landmarks.dat** in google

### Working

**1. Video Capture**
	- The webcam captures live video using OpenCV.

**2. Face & Eye Detection**
	- dlib’s get_frontal_face_detector() detects faces.
	- A pretrained model (shape_predictor_68_face_landmarks.dat) maps 68 facial landmarks.
	- Eye regions are extracted (left eye: points 36–41, right eye: points 42–47).

**3. Eye Aspect Ratio (EAR) Calculation**
	- Uses the Euclidean distance between eye landmarks.
	- EAR Formula:
		EAR = (||p2-p6|| + ||p3-p5|| ) / 2*||p1-p4||
	- If EAR < 0.25 (threshold), it means eyes are likely closed.

**4. Alert Mechanism**
	- Displays “DROWSINESS DETECTED” and “You are Sleeping Please Wake up!!” on the screen.
	- Uses pyttsx3 to speak the warning aloud.

**5. Exit Condition**
	- Program runs until the user presses 'q'.

### Key Libraries Used

1. **OpenCV** → video capture & drawing on frames.

2. **dlib** → face and landmark detection.

3. **scipy** → Euclidean distance for EAR.

4. **pyttsx3** → text-to-speech audio alert.

### Requirements

Install the following dependencies before running:
##### pip install opencv-python dlib scipy pyttsx3



Download the file and save it in your project folder, then run the project.

### How to Run
Run the script with :
**F5** or **python drowsiness.py**

When drowsiness is detected:
- A red warning message is displayed.
- A voice alert is spoken: "You are Sleeping Please wake up!!"
