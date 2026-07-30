# 🤟 Sign-To-Text: Real-Time ASL Recognition & Speech Translation

[![Hugging Face Spaces](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Live%20Demo-blue)](https://huggingface.co/spaces/Aritra907/S2T)
[![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.8%2B-5C3EE8?logo=opencv&logoColor=white)](https://opencv.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-FF6F00?logo=tensorflow&logoColor=white)](https://www.tensorflow.org/)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-0.10%2B-0097A7)](https://developers.google.com/mediapipe)

A vision-based Human-Computer Interface (HCI) designed to bridge the communication gap for the Deaf and Hard of Hearing community. This system captures real-time American Sign Language (ASL) fingerspelling gestures via a standard webcam, translates them into text, and vocalizes them using Text-to-Speech (TTS) synthesis.

---

## 🚀 Live Demo

Experience the live real-time translation model hosted on Hugging Face Spaces:  
 [Don't forget to hit the record button]
👉 **[Try the Interactive Demo](https://huggingface.co/spaces/Aritra907/S2T)**

---

## 🎯 Features

* **Real-Time Fingerspelling Recognition:** Detects and classifies ASL fingerspelling gestures (A–Z) instantly from a video stream.
* **Lighting & Background Agnostic:** Leverages landmark detection to eliminate background clutter and illumination dependency.
* **Hierarchical Gesture Classification:** Combines CNN feature extraction with mathematical landmark heuristics to maintain high accuracy across visually similar gestures.
* **Text-to-Speech (TTS) Output:** Converts predicted words into spoken audio using `pyttsx3` for seamless bi-directional dialogue.
* **Cost-Effective & Non-Invasive:** Operates entirely on standard webcams without requiring expensive gloved hardware or depth sensors.

---

## 🛠️ System Architecture & Methodology

[ Webcam Feed ] ➔ [ MediaPipe Hand Detection ] ➔ [ Landmark Skeleton Extraction ]
│
[ Text-to-Speech Output ] ◄── [ Mathematical Disambiguation ] ◄── [ CNN Gesture Classification ]

### 1. Data Acquisition & Preprocessing
Traditional vision-based approaches rely heavily on raw pixel segmentation, which breaks down in unpredictable environments (e.g., poor lighting or busy backgrounds). 

To overcome this:
1. **Hand Tracking:** MediaPipe extracts 21 key 3D hand landmarks in real time.
2. **Skeleton Normalization:** The landmarks are mapped onto a clean, uniform canvas.
3. **Robustness:** By training the model on skeletal representations rather than raw pixel matrices, the system remains background- and lighting-invariant.

### 2. Gesture Classification
Using a Convolutional Neural Network (CNN) built with Keras/TensorFlow, the skeletal images are processed through standard convolution, max-pooling, and dense layers.

To boost classification precision across 26 letters, visually similar gestures are grouped into 8 macro-classes, followed by mathematical landmark analysis to disambiguate the specific letter:

| Class Group | Alphabets | Disambiguation Strategy |
| :--- | :--- | :--- |
| **Group 1** | `[Y, J]` | Motion vector tracing & relative joint angles |
| **Group 2** | `[C, O]` | Curvature distance between thumb and index tips |
| **Group 3** | `[G, H]` | Horizontal finger extension counts |
| **Group 4** | `[B, D, F, I, U, V, K, R, W]` | Multi-finger extension geometry |
| **Group 5** | `[P, Q, Z]` | Downward orientation vectors |
| **Group 6** | `[A, E, M, N, S, T]` | Fist closure position relative to thumb |

### 3. Text-to-Speech Synthesis
Once individual characters are predicted and compiled into words, the `pyttsx3` library synthesizes the text into spoken audio, allowing non-signers to hear the translated message instantly.

---

## 📊 Performance & Results

* **Standard Environment (Clean background & good lighting):** ~**99%** Accuracy
* **Complex Real-World Environment (Dynamic background & variable lighting):** ~**97%** Accuracy

---

## 💻 Tech Stack & Requirements

### Hardware Requirements
* Standard HD Webcam

### Software & Libraries
* **Operating System:** Windows 8 or higher / Linux / macOS
* **IDE:** PyCharm / VS Code
* **Python Version:** Python 3.9+

| Package | Required Version |
| :--- | :--- |
| `opencv-python` | 4.8.0 |
| `mediapipe` | 0.10.11 |
| `numpy` | 1.25.1 |
| `tensorflow` / `keras` | 2.x |
| `pyttsx3` | Latest |

---

## ⚙️ Installation & Local Setup

1. **Clone the Repository:**
   ```bash
   git clone [https://github.com/your-username/Sign-To-Text.git](https://github.com/your-username/Sign-To-Text.git)
   cd Sign-To-Text

## 👨‍💻 Author

**Aritra Barman**
* GitHub: [@Aritra709](https://github.com/Aritra709)

 
## 🤝 Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".

1. **Fork** the Project
2. **Create** your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your Changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the Branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

---

## 📜 License

This project is open-source and available under the [MIT License](LICENSE).
