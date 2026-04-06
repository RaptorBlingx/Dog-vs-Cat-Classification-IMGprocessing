<div align="center">

# 🐶🐱 Dog vs. Cat Image Classification
### Using Transfer Learning & Image Processing Techniques

![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-Deep%20Learning-D00000?style=for-the-badge&logo=keras&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-Image%20Processing-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)

**Final Academic Project — Software Engineering Department | Image Processing Course**

</div>

---

## 📌 Project Overview

This project presents a binary image classification system capable of distinguishing between **dogs** and **cats** with high accuracy. It was developed as a **final academic project** for the *Image Processing* course in the Software Engineering department.

The system leverages **Transfer Learning** using Google's pre-trained **MobileNetV2** architecture (via TensorFlow Hub), combined with classical image processing techniques for preprocessing and normalization. The goal is to demonstrate a full end-to-end pipeline — from raw dataset ingestion to real-time image prediction.

---

## 🎯 Objectives

- Build a robust binary image classifier using deep learning and transfer learning.
- Apply image preprocessing techniques including resizing, color normalization, and format standardization.
- Evaluate model performance on a held-out test set.
- Implement a predictive system capable of classifying unseen images in real time.

---

## 🗂️ Repository Structure

```
Dog-vs-Cat-Classification-IMGprocessing/
│
├── Dog_vs_Cat_Classification_Img_Processing.ipynb   # Main Jupyter Notebook (full pipeline)
├── Dog vs Cat - Image Processing - Final Report.docx # Academic final report
├── Dog vs Cat script.docx                            # Project script / documentation
└── README.md                                         # Project documentation (this file)
```

---

## 🧠 Methodology

### 1. Dataset
The dataset used is the [Kaggle Dogs vs. Cats](https://www.kaggle.com/c/dogs-vs-cats) competition dataset, which contains **25,000 labeled images** of dogs and cats. For this project, a subset of **2,000 images** (1,000 dogs + 1,000 cats) was used to train and evaluate the model.

| Split       | Images |
|-------------|--------|
| Training    | 1,600  |
| Testing     | 400    |
| **Total**   | **2,000** |

### 2. Image Preprocessing
All images undergo the following preprocessing steps before being fed into the model:

- **Resizing** — All images are resized to **224 × 224 pixels** to match MobileNetV2's expected input dimensions.
- **Color Conversion** — Images are converted to **RGB** to ensure consistent channel structure.
- **Normalization** — Pixel values are scaled to the range **[0, 1]** by dividing by 255.
- **Array Conversion** — Images are converted to **NumPy arrays** for numerical processing.

### 3. Label Encoding

| Class | Label |
|-------|-------|
| Cat   | `0`   |
| Dog   | `1`   |

### 4. Model Architecture

The classification model uses **Transfer Learning** with **MobileNetV2** as the backbone:

```
Input (224×224×3)
       │
       ▼
MobileNetV2 Feature Extractor    ← Pre-trained on ImageNet (frozen)
       │
       ▼
Dense Layer (2 units)            ← Custom classification head
       │
       ▼
Output: Cat (0) / Dog (1)
```

- **Base Model:** [`google/tf2-preview/mobilenet_v2/feature_vector/4`](https://tfhub.dev/google/tf2-preview/mobilenet_v2/feature_vector/4) (via TensorFlow Hub)
- **Trainable Layers:** Base model weights are **frozen**; only the dense head is trained.
- **Optimizer:** Adam
- **Loss Function:** Sparse Categorical Crossentropy (with logits)
- **Metric:** Accuracy
- **Epochs:** 5

---

## 🛠️ Technologies & Libraries

| Library / Framework   | Purpose                                      |
|-----------------------|----------------------------------------------|
| `TensorFlow 2.x`      | Model building, training, and evaluation     |
| `TensorFlow Hub`      | Loading the pre-trained MobileNetV2 model    |
| `Keras`               | High-level neural network API                |
| `OpenCV (cv2)`        | Image reading and resizing                   |
| `Pillow (PIL)`        | Image resizing and format conversion         |
| `NumPy`               | Numerical array operations                   |
| `Matplotlib`          | Image visualization                          |
| `scikit-learn`        | Train/test splitting                         |
| `Kaggle API`          | Dataset download                             |

---

## 🚀 Getting Started

### Prerequisites

Ensure you have **Python 3.8+** installed. Install the required dependencies:

```bash
pip install tensorflow tensorflow-hub opencv-python pillow numpy matplotlib scikit-learn kaggle
```

### Dataset Setup

1. Obtain your Kaggle API credentials (`kaggle.json`) from [kaggle.com/account](https://www.kaggle.com/account).
2. Place `kaggle.json` in the project directory.
3. Run the first cells of the notebook to download and extract the dataset:

```bash
kaggle competitions download -c dogs-vs-cats
```

### Running the Notebook

Launch the Jupyter Notebook:

```bash
jupyter notebook Dog_vs_Cat_Classification_Img_Processing.ipynb
```

Execute the cells sequentially from top to bottom to:
1. Download and extract the dataset
2. Preprocess and resize images
3. Encode labels
4. Build and train the model
5. Evaluate performance
6. Run predictions on new images

---

## 📊 Results

The model was trained for **5 epochs** on 1,600 images and evaluated on 400 test images.

| Metric         | Value        |
|----------------|--------------|
| Training Split | 80% (1,600)  |
| Testing Split  | 20% (400)    |
| Epochs         | 5            |
| Optimizer      | Adam         |

> ✅ The transfer learning approach with MobileNetV2 allows the model to achieve strong classification performance even with a relatively small training dataset, thanks to rich feature representations pre-learned on ImageNet.

---

## 🔍 Predictive System

After training, the model includes an interactive **predictive system** that accepts an image path and outputs the classification result:

```
Path of the image to be predicted: /path/to/your/image.jpg
```

**Output Example:**
```
The image represents a Dog 🐶
```
or
```
The image represents a Cat 🐱
```

---

## 📄 Academic Report

The full academic report (`Dog vs Cat - Image Processing - Final Report.docx`) covers:
- Problem definition and motivation
- Literature review of image classification methods
- Detailed methodology and system design
- Experimental results and analysis
- Conclusions and future work

---

## 👨‍💻 Authors

This project was developed as a **final academic project** for the:

> 🎓 **Software Engineering Department** — Image Processing Course

---

## 📜 License

This project is intended for **academic and educational purposes only**.  
Dataset credits: [Kaggle — Dogs vs. Cats Competition](https://www.kaggle.com/c/dogs-vs-cats)

---

<div align="center">

*Built with ❤️ using TensorFlow, MobileNetV2, and classical image processing techniques.*

</div>
