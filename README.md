# 🎭 DeepFake Detection System

## 📌 Table of Contents
1. [Introduction](#introduction)  
2. [Impact of DeepFake Videos](#impact-of-deepfake-videos)  
3. [Project Objectives](#project-objectives)  
4. [System Architecture](#system-architecture)  
5. [Pre-processing Workflow](#pre-processing-workflow)  
6. [Prediction Workflow](#prediction-workflow)  
7. [Models Used](#models-used)  
8. [Hyperparameters](#hyperparameters)  
9. [Deployment](#deployment)  
10. [Installation & Usage](#installation--usage)  
11. [Technologies Used](#technologies-used)  
12. [Future Improvements](#future-improvements)  
13. [Conclusion](#conclusion)  

## 📖 Introduction

**DeepFakes** are synthetic media in which a person’s likeness is manipulated using AI techniques such as **Generative Adversarial Networks (GANs)**. These videos can be misleading and nearly indistinguishable from authentic footage.

This project presents a DeepFake detection system utilizing:

- **VGG16** for visual feature extraction  
- **CNN** for frame-wise classification  
- **Dlib** for facial landmark detection  
- **OpenCV** for frame processing and face detection  

## 🌐 Impact of DeepFake Videos

- **Misinformation & Propaganda**: Spread of fake news, altering public opinion.  
- **Celebrity & Political Scams**: Used in impersonation or defamation campaigns.  
- **Security & Privacy Breaches**: Threats to biometric authentication systems.  

## 🎯 Project Objectives

- Develop an AI-powered system to detect DeepFake videos.
- Use **OpenCV** to extract frames and detect faces.
- Apply **Dlib** to extract facial landmarks for tampering evidence.
- Use **VGG16** for deep feature extraction and a **CNN** to classify video frames.
- Aggregate frame-level predictions to classify an entire video.
- Deploy a user-friendly interface for real-time detection.

## 🛠️ System Architecture

```
Upload Video → Extract Frames → Face Detection (OpenCV) → Landmark Detection (Dlib) → Feature Extraction (VGG16) → CNN Classification → Aggregate Predictions → Real/Fake
```

## 🔄 Pre-processing Workflow

1. Convert input video to frames using **OpenCV**.  
2. Detect faces in each frame.  
3. Use **Dlib** to extract **68 facial landmarks**.  
4. Resize all faces to `224×224` pixels.  
5. Normalize the pixel values.  
6. Store features and landmark metadata for model input.

## 🔍 Prediction Workflow

1. User uploads a video via frontend.  
2. Backend extracts frames and processes them with OpenCV.  
3. **Dlib** landmarks are used to check inconsistencies in facial movements.  
4. **VGG16** extracts frame features.  
5. Frames are passed through the trained **CNN**.  
6. Frame-level predictions are aggregated using a majority vote or average score.  
7. Final classification (Real or Fake) is returned to the user.

## 🧠 Models Used

### VGG16 (Feature Extractor)
- Pre-trained on ImageNet.
- Fine-tuned for facial feature sensitivity.
- Outputs high-dimensional feature vectors.

### CNN (Classifier)
- **Conv + Pooling Layers** for spatial analysis.  
- **Fully Connected Layers** for binary classification.  
- **Activation**: Sigmoid for probability output.

## ⚙️ Hyperparameters

| Parameter        | Value             |
|------------------|------------------|
| Optimizer        | Adam             |
| Learning Rate    | 0.0001           |
| Loss Function    | focal_loss       |
| Batch Size       | 32               |
| Epochs           | 35               |
| Accuracy Achieved| 85%              |


## 🚀 Deployment

- **Backend**: Flask (Python-based REST API)  
- **Frontend**: HTML, CSS, JavaScript  
- **Processing Time**: ~1 minute for a 10-second, 30fps video  

## 🧪 Installation & Usage

### Step 1: Clone Repository and Install Dependencies
```bash
git clone <repo-url>
cd deepfake-detector
pip install -r requirements.txt
```

### Step 2: Run the Flask App
```bash
python app.py
```

### Step 3: Upload a Video
- Navigate to `http://localhost:5000`  
- Upload a video for classification  
- View output: **Real** or **Fake**

## 💻 Technologies Used

| Category         | Tools & Libraries                         |
|------------------|-------------------------------------------|
| Programming      | Python, HTML, CSS, JavaScript             |
| Libraries        | OpenCV, Dlib, TensorFlow, Keras, NumPy    |
| Models           | VGG16, Custom CNN                         |
| Deployment       | Flask Web Framework                       |

## 🔮 Future Improvements

- Fine-tune deeper VGG16 layers for improved discrimination.  
- Expand dataset with diverse ethnicities, lighting, and angles.  
- Integrate **LSTM** or **3D-CNN** for capturing temporal features.  
- Add batch video processing and real-time webcam detection.  
- Improve frontend UI for better user experience.

## ✅ Conclusion

This project successfully implements a DeepFake Detection system combining:

- **OpenCV** for frame & face extraction  
- **Dlib** for facial landmark detection  
- **VGG16** for feature extraction  
- **CNN** for classification  

With an accuracy of **85%**, the system shows high potential for applications in **media validation**, **social platforms**, and **digital forensics**.

Further improvements will enhance model robustness and real-time performance.

Further improvements could be made by fine-tuning VGG16 layers, increasing dataset diversity, and integrating LSTM for temporal analysis.
