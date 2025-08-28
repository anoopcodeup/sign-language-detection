# 🤟 Real-Time Sign Language Recognition

A real-time sign language detection system that uses a webcam to capture gestures and an LSTM deep learning model to classify them. This project leverages MediaPipe for high-fidelity keypoint extraction and TensorFlow for sequence-based gesture prediction, providing an interactive and responsive experience.

---

## ✨ Features

-   **Real-Time Gesture Detection**: Classifies sign language gestures directly from a live webcam feed.
-   **High-Fidelity Keypoint Extraction**: Utilizes MediaPipe Holistic to detect 543 landmarks across the body, face, and hands for robust feature creation.
-   **Temporal Sequence Modeling**: Employs a Long Short-Term Memory (LSTM) network to understand and classify dynamic gestures based on a sequence of frames.
-   **Intuitive UI**: Overlays keypoint data and the currently recognized sign directly onto the video feed for immediate visual feedback.
-   **Modular & Maintainable Code**: The backend logic is organized into separate modules for constants, utilities, and the main application loop, making the codebase clean and easy to extend.
-   **Prediction Smoothing**: Implements a confidence threshold and prediction history to prevent flickering and ensure stable, reliable gesture classification.

---

## 📁 Project Structure

```
.
├── main.py             # Main script to run the application
├── utils.py            # Helper functions for MediaPipe, keypoint extraction, etc.
├── constants.py        # All constant values (actions, colors, thresholds)
├── requirements.txt    # Project dependencies
└── model.h5            # Pre-trained Keras model for gesture classification
```

---

## ⚙️ Requirements

-   Python 3.8+
-   TensorFlow
-   OpenCV
-   MediaPipe
-   NumPy

Install all required Python dependencies with:

```bash
pip install -r requirements.txt
```

---

## 🚀 Usage

### 1. Clone the Repository

```bash
git clone https://github.com/anoopcodeup/sign-language-detection.git
cd sign-language-detection
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Ensure Model is Present

Make sure the pre-trained model file, `model.h5`, is located in the root directory of the project.

### 4. Run the Application

```bash
python main.py
```

The application will start, open your webcam, and begin detecting gestures in real-time. Press the 'q' key to quit.

---

## ✍️ How It Works

The application follows a real-time processing pipeline:

1.  **Video Capture**: OpenCV captures video from the default webcam, frame by frame.
2.  **Keypoint Detection**: Each frame is passed to the MediaPipe Holistic model, which detects and returns the 3D coordinates of all 543 landmarks.
3.  **Feature Extraction**: The coordinates of the keypoints are flattened into a single NumPy array, creating a feature vector for that frame.
4.  **Sequence Creation**: The application collects the feature vectors from the last 30 frames to form a sequence, which represents a short, time-dependent action.
5.  **Prediction**: Once a 30-frame sequence is complete, it is fed into the pre-trained LSTM model, which predicts the most likely gesture ('hello', 'thanks', or 'iloveyou').
6.  **Visualization**: The predicted gesture is displayed on the screen. To improve stability, a prediction is only shown if it is consistent over the last 10 frames and exceeds a confidence threshold.

---

## 🛠 Future Improvements

-   **Expand Vocabulary**: Train the model on a larger dataset to recognize a wider range of sign language gestures.
-   **GUI Application**: Develop a more advanced user interface using a framework like Streamlit or PyQt to add more features and controls.
-   **Performance Optimization**: Investigate model quantization or hardware acceleration to improve performance on less powerful devices.
-   **Custom Datasets**: Build a data collection script to allow users to easily record and train the model on their own custom gestures.

---

## 📚 References

-   TensorFlow: [tensorflow.org](https://tensorflow.org)
-   OpenCV: [opencv.org](https://opencv.org)
-   MediaPipe: [ai.google.dev/edge/mediapipe](https://ai.google.dev/edge/mediapipe)
