Real-Time Hand Gesture Recognition
Hi! This is a project I built to explore how Computer Vision and Machine Learning can work together to understand human movement. Using just a standard webcam, this app detects hand landmarks in real-time and classifies them into specific gestures.

🚀 Project Overview
The goal of this project was to create a lightweight system that can recognize:

Static Hand Signs: Identifying a specific shape (like a fist or an open palm) in a single frame.

Dynamic Finger Gestures: Identifying a movement over time (like waving or clockwise/counter-clockwise circles).

🛠️ How it Works (The Technical Stuff)
I broke the system down into a three-step pipeline:

1. Hand Tracking with MediaPipe
Instead of analyzing every single pixel in a video frame, I use MediaPipe to find 21 specific "landmarks" (joints) on the hand. This makes the processing much faster and more efficient.

2. Data Normalization
A big challenge in gesture recognition is making sure the AI doesn't get confused if your hand is far away or tilted. I implemented a preprocessing step that:

Converts landmarks to relative coordinates based on the wrist.

Normalizes the coordinates to a standard scale.

Flattens the data so it can be fed into a Neural Network.

3. Classification with TensorFlow/TFLite
KeyPoint Classifier: A simple Multi-Layer Perceptron (MLP) that takes the 21 landmarks and predicts the hand sign.

Point History Classifier: A model that looks at the last 16 frames of your index finger's movement to recognize "motion" gestures. This can even be configured to use an LSTM (Long Short-Term Memory) network for better sequence recognition.

📂 Folder Structure
app.py: The main entry point to run the webcam demo.

keypoint_classification_EN.ipynb: The notebook I used to train the hand sign model.

point_history_classification.ipynb: The notebook for training the movement gestures.

model/: Contains the trained TFLite models and the label files.

🏃 How to Run it
First, make sure you have the requirements installed:

Bash
pip install mediapipe opencv-python tensorflow
Then, just run the main script:

Bash
python app.py
📈 Learning Outcomes
Through this project, I learned how to:

Process real-time video streams using OpenCV.

Work with Landmark Detection models.

Prepare and normalize datasets for Neural Networks.

Deploy models as TFLite for better performance on laptops
