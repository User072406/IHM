# Traffic Sign Detection and Classification on the GTSRB Dataset

## Overview

This project addresses the problem of **traffic sign detection and classification** using the **German Traffic Sign Recognition Benchmark (GTSRB)** dataset. The goal is to develop a model that can both detect the **bounding box** of traffic signs in images and classify them into **one of 43 traffic sign classes**.

This capability is highly valuable for **autonomous driving systems**, where real-time recognition of road signs is critical for safe navigation.

---

## Dataset

- **Dataset**: GTSRB (German Traffic Sign Recognition Benchmark)
- **Annotations**: Image paths, bounding box coordinates (Roi.X1, Roi.Y1, Roi.X2, Roi.Y2), and class labels (0-42).
- **Data Preprocessing**:
  - Resized all images to **224x224**.
  - Scaled bounding box coordinates to match resized images.
  - Split dataset into **80\% training** and **20\% validation**.
  - Provided utilities to visualize bounding boxes and labels.

---

## Model Architecture

The model leverages a **pretrained MobileNetV2 backbone** for feature extraction and includes:

- **Bounding Box Regressor**: Predicts bounding box coordinates (x1, y1, x2, y2).
- **Classifier**: Predicts one of 43 traffic sign classes.

Both heads share the backbone and are followed by adaptive pooling and fully connected layers.

---

## Loss Function

A **composite loss function** is used:

- **Smooth L1 Loss** for bounding box regression.
- **Cross-Entropy Loss** for classification.

This combination balances localization accuracy and class prediction.

---

## Training Configuration

- **Optimizer**: Adam
- **Learning Rate**: 1e-4
- **Batch Size**: 8
- **Early Stopping**: Based on validation loss with patience of 5
- **Loss Tracking**: Plotted training and validation loss curves

---

## Results

### Validation Results
- **Training converged** in 19 epochs.
- **Qualitative results** showed accurate bounding box placement and correct classification.

### Test Results
- **Test Loss**: 1.3539
- **Classification Accuracy**: **98.99\%**
- **Average IoU**: **0.9589**

---

## Example Predictions

Predictions on validation and test samples showed strong alignment between **predicted** and **ground truth** bounding boxes and labels.

---

## Limitations and Future Work

- Currently supports **single sign detection per image**.
- No **real-time video inference** yet.
- Future improvements:
  - **Multi-object detection**.
  - **Real-time deployment** on video streams.
  - **Generalization** to other datasets like **GTSDB**.

---

## Conclusion

This project demonstrates a full deep learning pipeline for **traffic sign detection and classification** with high performance on the GTSRB dataset. The results indicate readiness for scaling to more complex scenarios such as **real-time traffic sign recognition** in video data.
