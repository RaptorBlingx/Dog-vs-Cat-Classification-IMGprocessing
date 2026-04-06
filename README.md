<div align="center">

# 🐶 Dog vs Cat Classification
### Image Processing & Deep Learning — Academic Final Project

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange?style=for-the-badge&logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-Transfer%20Learning-red?style=for-the-badge&logo=keras&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-Image%20Processing-green?style=for-the-badge&logo=opencv&logoColor=white)
![Kaggle](https://img.shields.io/badge/Kaggle-Dataset-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)
![License](https://img.shields.io/badge/License-Academic-lightgrey?style=for-the-badge)

> **Binary image classification** system that distinguishes between dogs and cats using Transfer Learning on a MobileNetV2 backbone — developed as an academic final project for the Software Engineering Department.

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Project Structure](#-project-structure)
- [Dataset](#-dataset)
- [Methodology](#-methodology)
- [Model Architecture](#-model-architecture)
- [Results](#-results)
- [Tech Stack](#-tech-stack)
- [Getting Started](#-getting-started)
- [Usage](#-usage)
- [Academic Context](#-academic-context)

---

## 🔍 Overview

This project implements a **binary image classifier** capable of distinguishing between dog and cat images with high accuracy. It leverages **Transfer Learning** using the pre-trained **MobileNetV2** model from TensorFlow Hub, fine-tuned on the Kaggle Dogs vs. Cats competition dataset.

The pipeline covers the full machine learning workflow:
- Dataset acquisition via Kaggle API
- Image preprocessing and normalization
- Feature extraction with a frozen MobileNetV2 backbone
- Custom classification head training
- Real-time image prediction system

---

## 📁 Project Structure

```
Dog_vs_Cat-Classification-ImgProcessing/
│
├── Dog_vs_Cat_Classification_Img_Processing.ipynb   # Main Jupyter Notebook
├── Dog vs Cat - Image Processing - Final Report.docx # Academic Final Report
├── Dog vs Cat script.docx                           # Project Script / Documentation
└── README.md                                        # Project Documentation
```

---

## 📦 Dataset

| Property | Details |
|----------|---------|
| **Source** | [Kaggle Dogs vs. Cats Competition](https://www.kaggle.com/c/dogs-vs-cats) |
| **Total Images Used** | 2,000 (sampled from 25,000) |
| **Training Set** | 1,600 images (80%) |
| **Test Set** | 400 images (20%) |
| **Image Format** | JPEG / PNG |
| **Resized Dimensions** | 224 × 224 × 3 (RGB) |

**Class Labels:**
| Label | Class |
|-------|-------|
| `0` | Cat 🐱 |
| `1` | Dog 🐶 |

---

## 🔬 Methodology

The project follows a structured machine learning pipeline:

```
1. Data Acquisition       →  Kaggle API download
2. Dataset Extraction     →  Unzip & organize train images
3. Image Preprocessing    →  Resize to 224×224, convert to RGB
4. Label Encoding         →  Cat = 0, Dog = 1
5. Numpy Array Conversion →  cv2 + glob → NumPy arrays
6. Train/Test Split       →  80% train / 20% test
7. Normalization          →  Pixel values scaled to [0, 1]
8. Model Building         →  MobileNetV2 + Dense classification head
9. Model Training         →  Adam optimizer, 5 epochs
10. Evaluation            →  Accuracy & Loss on test set
11. Prediction            →  Real-time inference on custom images
```

---

## 🧠 Model Architecture

```
┌──────────────────────────────────────────────────────┐
│                    Input Layer                       │
│                (224 × 224 × 3)                       │
└────────────────────────┬─────────────────────────────┘
                         │
┌────────────────────────▼─────────────────────────────┐
│             MobileNetV2 Feature Extractor            │
│     (Pre-trained on ImageNet — weights frozen)       │
│            Output: 1280-dim feature vector           │
└────────────────────────┬─────────────────────────────┘
                         │
┌────────────────────────▼─────────────────────────────┐
│              Dense Layer (2 units)                   │
│               (Classification Head)                  │
└────────────────────────┬─────────────────────────────┘
                         │
┌────────────────────────▼─────────────────────────────┐
│        SparseCategoricalCrossentropy (Logits)        │
│                 Adam Optimizer                       │
└──────────────────────────────────────────────────────┘
```

| Hyperparameter | Value |
|----------------|-------|
| Backbone | MobileNetV2 (TF Hub) |
| Backbone Trainable | `False` (frozen) |
| Classification Head | Dense(2) |
| Optimizer | Adam |
| Loss Function | SparseCategoricalCrossentropy |
| Epochs | 5 |
| Batch Size | Default (TensorFlow) |
| Input Shape | (224, 224, 3) |

---

## 📊 Results

The model was evaluated on a held-out test set of **400 images** after training for 5 epochs:

| Metric | Value |
|--------|-------|
| Training Split | 1,600 images |
| Test Split | 400 images |
| Epochs | 5 |
| Evaluation Metrics | Accuracy, Loss |

> Detailed results and analysis are available in the **Final Report** (`Dog vs Cat - Image Processing - Final Report.docx`).

---

## 🛠 Tech Stack

| Category | Library / Tool |
|----------|---------------|
| Language | Python 3.8+ |
| Deep Learning | TensorFlow 2.x, Keras |
| Transfer Learning | TensorFlow Hub (MobileNetV2) |
| Image Processing | OpenCV (`cv2`), Pillow (`PIL`) |
| Data Manipulation | NumPy |
| Visualization | Matplotlib |
| ML Utilities | scikit-learn |
| Dataset Source | Kaggle API |
| Development Environment | Google Colab / Jupyter Notebook |

---

## 🚀 Getting Started

### Prerequisites

Ensure you have Python 3.8+ and the following libraries installed:

```bash
pip install tensorflow tensorflow-hub opencv-python pillow numpy matplotlib scikit-learn kaggle
```

### Kaggle API Setup

1. Go to [kaggle.com](https://www.kaggle.com) → Account → **Create New API Token**
2. Download `kaggle.json` and place it in your project directory
3. Run the configuration cells in the notebook:

```python
!mkdir -p ~/.kaggle
!cp kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json
```

### Download the Dataset

```bash
kaggle competitions download -c dogs-vs-cats
```

---

## 💻 Usage

### Running the Notebook

1. Clone this repository:
   ```bash
   git clone https://github.com/RaptorBlingx/Dog_vs_Cat-Classification-ImgProcessing.git
   cd Dog_vs_Cat-Classification-ImgProcessing
   ```

2. Open the notebook in Google Colab or Jupyter:
   ```bash
   jupyter notebook Dog_vs_Cat_Classification_Img_Processing.ipynb
   ```

3. Follow the cells sequentially from dataset extraction through model training.

### Predicting a Custom Image

After training the model, use the built-in prediction system:

```python
input_image_path = input('Path of the image to be predicted: ')

input_image = cv2.imread(input_image_path)
input_image_resize = cv2.resize(input_image, (224, 224))
input_image_scaled = input_image_resize / 255
image_reshaped = np.reshape(input_image_scaled, [1, 224, 224, 3])

input_prediction = model.predict(image_reshaped)
input_pred_label = np.argmax(input_prediction)

if input_pred_label == 0:
    print('The image represents a Cat 🐱')
else:
    print('The image represents a Dog 🐶')
```

---

## 🎓 Academic Context

| Field | Details |
|-------|---------|
| **Project Type** | Academic Final Project |
| **Department** | Software Engineering |
| **Subject Area** | Image Processing & Computer Vision |
| **Technique** | Transfer Learning (MobileNetV2) |
| **Problem Type** | Binary Image Classification |

This project was submitted as a final project for the **Software Engineering Department**, demonstrating the application of deep learning and image processing techniques to solve a classical computer vision problem. The project includes:

- **Final Report**: `Dog vs Cat - Image Processing - Final Report.docx` — Comprehensive documentation of the project including background research, methodology, experimental results, and conclusions.
- **Script Documentation**: `Dog vs Cat script.docx` — Supporting script and step-by-step walkthrough of the implementation.
- **Notebook**: `Dog_vs_Cat_Classification_Img_Processing.ipynb` — Full runnable implementation.

---

<div align="center">

Made with ❤️ as an Academic Final Project — Software Engineering Department

</div>
