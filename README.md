# Sign Language Recognition System

This Sign Language Recognition System uses a combination of computer vision and machine learning techniques to translate sign language gestures into text and speech in real-time. The system is built using Python, leveraging OpenCV for video capture and processing, MediaPipe for gesture recognition, and TensorFlow for implementing and training deep learning models.

## Features

- **Real-Time Gesture Recognition**: Translates sign language gestures captured by a webcam into text and speech dynamically.
- **Deep Learning Model**: Utilizes Long Short-Term Memory (LSTM) networks to capture the temporal dependencies of gesture sequences.
- **Enhanced Visualization**: Incorporates styled landmarks visualization for better understanding and debugging.
- **Speech Output**: Converts recognized gestures to speech to make interactions intuitive and accessible.

## Software and Tools

- Python 3.8+
- OpenCV (cv2)
- MediaPipe
- TensorFlow 2.x
- Numpy
- Matplotlib (for debugging/visualization)
- pyttsx3 (for text-to-speech conversion)

## Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/n-mandadapu/sign-language-recognition.git
   cd sign-language-recognition
   ```

2. **Set up a virtual environment (optional but recommended):**

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. **Install the dependencies:**

   ```bash
   pip install -r requirements.txt
   ```

## Usage

To start the sign language recognition, execute the main script:

```bash
python sign_language_recognition.py
```

This script initializes the webcam and starts the sign language recognition in real-time. To terminate the session, simply press `q` while the program's window is active.

### Main Functionalities

1. **Video Capture**: Uses the computer's webcam to capture live video frames.
   
2. **Feature Extraction**: Utilizes MediaPipe to extract key landmarks from the captured video frames that represent the signer's hands, pose, and facial expressions.

3. **Landmark Styling**: Draws connections between extracted landmarks using styled lines and points to visualize the gestures dynamically.

4. **Gesture Classification**: Employs an LSTM model to classify the extracted gesture sequences into predefined categories like "hello," "thank you," etc.

5. **Text and Speech Output**: The recognized gestures are displayed as text on the screen and are also spoken aloud using a text-to-speech engine.

### Examples

- **Starting the Recognition**:
  
  The system will start and the webcam feed will appear in a window. Perform sign language gestures within the view of the camera. The recognized gestures will be displayed as text and spoken using your system's speakers.

- **Exiting the Program**:

  Press 'q' to quit the program. The webcam will be deactivated and the window will close.

## Configuration

The system's sensitivity and performance can be adjusted by modifying the `min_detection_confidence` and `min_tracking_confidence` parameters in the `Holistic` model configuration:

```python
with mp_holistic.Holistic(min_detection_confidence=0.5, min_tracking_confidence=0.5) as holistic:
```

Increasing these values will require higher confidence in the detections and tracking, potentially reducing false positives but requiring clearer gestures.

## Data Collection

For training new models or retraining the provided models with new data:

- Collect gesture data by executing the `collect_data` cell.
- Label the data according to the gestures performed.
- Use the `train_model` cell to train the model using the collected data.

The training process and the model's performance can be monitored using TensorBoard:

```bash
tensorboard --logdir=Logs
```

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

---
