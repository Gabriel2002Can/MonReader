# MonReader

**Computer Vision for Automated Document Orientation Detection**  
*A Keras/TensorFlow CNN model to detect flipped document pages (and support corner-aware preprocessing with contrast sharpening) for high-speed digitization workflows.*

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=flat-square&logo=python)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange?style=flat-square&logo=tensorflow)
![Keras](https://img.shields.io/badge/Keras-3.x-orange?style=flat-square&logo=keras)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat-square&logo=jupyter)

---

## Table of Contents

1. [Executive Summary](#executive-summary)
2. [Project Background](#project-background)
3. [Problem Statement](#problem-statement)
4. [Dataset Overview](#dataset-overview)
5. [Step-by-Step Project Workflow](#step-by-step-project-workflow)
6. [Technologies & Tools](#technologies--tools)
7. [Key Results & Insights](#key-results--insights)
8. [Business Impact](#business-impact)
9. [How to Reproduce](#how-to-reproduce)
10. [Conclusion](#conclusion)
11. [For Hiring Managers & Recruiters](#for-hiring-managers--recruiters)

---

## Executive Summary

This end-to-end computer vision project, completed as part of the **Apziva** AI Residency, builds a robust binary classifier to automatically detect whether a scanned document page is being flipped (“flip”) or not (“notflip”). 

Using a custom image dataset, the model addresses real-world digitization challenges and incorporates preprocessing steps such as normalization and resizing The final **Keras/TensorFlow CNN** delivers fast, accurate predictions that can be integrated into high-speed scanning pipelines.

The complete pipeline (data loading → exploration → preprocessing → modeling → evaluation → inference) is implemented in a clean, reproducible Jupyter notebook.

---

## Project Background
**MonReader** is a mobile document digitization app for fully automatic, high-speed, high-quality bulk scanning. Users simply flip pages while the app automatically detects page flips from the low-resolution camera preview, captures a high-resolution picture, recognizes corners to crop the document, dewarps it for a bird’s-eye view, sharpens contrast, recognizes text with formatting intact, and applies ML-powered redaction.

This repository implements the core Keras/TensorFlow CNN model for page-flip detection, which predicts whether a page is being flipped using a single image frame.

---

## Problem Statement

> **“Is this page being flipped right now?”**

**Key challenges:**
- Variable lighting, contrast, and document layouts
- Need for real-time inference on high-speed scanners
- Robustness to partial occlusions or corner artifacts
- Balancing precision/recall to minimize both false positives (unnecessary corrections) and false negatives (missed flips)

---

## Dataset Overview

**Source**: Custom image collection stored in the `images/` folder (training and testing subdirectories).

**Classes** (2 total):
- `flip` — pages are being flipped
- `notflip` — pages are static

**Dataset Size**:
- Training: 2,392 images (80/20 train/validation split)
- Validation: 478 images
- Testing: 597 images

Images are automatically resized to **128×128** pixels during loading. A preview of the class structure is available directly in the notebook (sample images shown in the `images/` folder).

---

## Step-by-Step Project Workflow

The entire pipeline is fully documented in `MonReader_TF.ipynb`.

### 1. Data Ingestion
- Loaded image datasets using `image_dataset_from_directory`
- Configured batch size (32) and image size (128×128) with reproducibility seed

### 2. Exploratory Data Analysis (EDA)
- Verified class distribution (“flip” vs “notflip”)
- Visualized sample images from each class
- Inspected dataset balance and image characteristics

### 3. Data Preprocessing
- Automatic resizing and batching
- Built-in support for contrast sharpening and corner-aware handling (integrated in the workflow)

### 4. Model Development
- Defined a convolutional neural network (CNN) using Keras/TensorFlow
- Binary classification output (flip / notflip)

### 5. Training
- Trained the CNN on the training split
- Monitored validation performance

### 6. Evaluation & Validation
- Computed business-relevant metrics: accuracy, F1-score, ROC-AUC, confusion matrix, and classification report
- Analyzed train/validation/test generalization

### 7. Inference
- Loaded the trained model for single-image or batch predictions
- Ready for integration into production digitization pipelines

---

## Technologies & Tools

| Category          | Technologies                                      |
|-------------------|---------------------------------------------------|
| Language          | Python 3                                          |
| Deep Learning     | TensorFlow, Keras                                 |
| Data Handling     | tensorflow.keras.preprocessing.image              |
| Visualization     | Matplotlib, scikit-learn                          |
| Evaluation        | scikit-learn (metrics, confusion matrix)          |
| Environment       | Jupyter Notebook                                  |
| Other             | Git, GitHub                                       |

---

## Key Results & Insights

**Model Performance (Test Set)**:
- Strong binary classification between flipped and not flipped
- High F1-score and ROC-AUC, confirming reliable detection even under varying contrast and layout conditions
- Confusion matrix and classification report available in the notebook for detailed analysis

**Key Insights**:
- Convolutional layers effectively capture edge and corner patterns critical for orientation detection
- Contrast sharpening preprocessing noticeably improves model robustness on real-world scanned documents
- The lightweight CNN architecture enables fast inference suitable for high-speed digitization pipelines

---

## Business Impact

- **Time Savings**: Eliminates manual orientation checks for thousands of pages per batch
- **Cost Reduction**: Reduces labor in digitization centers and back-office operations
- **Scalability**: Model can be deployed as a real-time preprocessing step in scanning hardware or cloud workflows
- **Accuracy**: Near-zero tolerance for missed flips, ensuring high-quality digitized archives

---

## How to Reproduce

Clone the repository:

   ```bash
   # 1. Clone the repository (default branch is keras_branch)
   git clone https://github.com/Gabriel2002Can/MonReader.git
   cd MonReader

   # 2. Install dependencies
   pip install tensorflow keras matplotlib scikit-learn

   # 3. Launch notebook
   jupyter notebook MonReader_TF.ipynb
   ```

 The images/ folder is included with the full dataset, so the notebook runs out-of-the-box.

 ---

 ## Conclusion
This project implements a Keras/TensorFlow CNN binary classifier for detecting page flips from single image frames. The model is trained on frames extracted from smartphone videos labeled as flipping or notflipping and evaluated primarily on F1-score.
It serves as the trigger for the full automated pipeline: high-resolution capture, corner detection, cropping, dewarping, contrast sharpening, OCR, and ML redaction.

---

 ## For Hiring Managers & Recruiters
 What this project demonstrates about my capabilities:

- **End-to-End Computer Vision Pipeline Ownership:** From raw image directories to trained inference-ready model — no hand-holding required.
- **Deep Learning for Image Classification:** Designed, trained, and evaluated a custom Keras/TensorFlow CNN tailored to a real business problem.
- **Production-Focused Mindset:** Emphasized preprocessing (normalization, rescaling), business metrics (F1, ROC-AUC), and fast inference over raw accuracy.
- **Reproducible & Deployable Code:** Clean Jupyter notebook with clear workflow, ready for scaling into production digitization systems.
- **Full-Stack AI Skillset:** Combines strong Python/ML engineering with practical domain knowledge in document processing workflows.
