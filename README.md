# HelmetDector: Real-Time Computer Vision for Safety Compliance

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.0+-orange.svg)](https://opencv.org/)
[![Deep Learning](https://img.shields.io/badge/Framework-YOLOv8/PyTorch-red.svg)](https://pytorch.org/)

## Executive Summary
**HelmetDector** is an intelligent surveillance solution designed to automate the monitoring of safety helmet compliance in high-risk environments, such as construction sites and traffic systems. Utilizing state-of-the-art object detection algorithms, this project identifies individuals and classifies them based on safety gear adherence in real-time.

This project transitions from theoretical computer vision to practical application, addressing the "last-mile" problem of safety enforcement through automated visual inspection.

---

## Technical Architecture

The system utilizes a deep learning pipeline optimized for inference speed and accuracy.

### Core Pipeline:
1.  **Frame Acquisition**: High-frequency video stream ingestion via OpenCV.
2.  **Preprocessing**: Spatial resizing and normalization to match the model's input tensor requirements.
3.  **Inference Engine**: A convolutional neural network (CNN) backbone (e.g., YOLOv8 or Faster R-CNN) performs simultaneous localization and classification.
4.  **Post-Processing**: Non-Maximum Suppression (NMS) is applied to eliminate redundant bounding box overlaps and refine detection confidence.

### Model Classes:
* `With Helmet`: Identification of compliant individuals.
* `Without Helmet`: Identification of safety violations.
* `Person`: (Optional) Base detection to establish context before classification.

---

## Performance Metrics & Evaluation

To ensure academic rigor, the model is evaluated using standard Computer Vision benchmarks:

* **mAP @ 0.5**: Mean Average Precision at a 0.5 Intersection over Union (IoU) threshold.
* **Precision/Recall Trade-off**: Optimized to minimize False Negatives (missing a person without a helmet), which is the most critical error in a safety context.
* **Inference Latency**: Measured in Milliseconds (ms) per frame to ensure the system meets real-time processing requirements ($>30$ FPS).

---

## Key Features

* **Real-Time Detection**: Optimized weights for deployment on edge devices or GPU-accelerated environments.
* **Automated Alerting**: (If applicable) Logic to trigger visual or logged alerts upon detection of a violation.
* **Robustness**: Trained on diverse datasets to handle varying lighting conditions, occlusions, and camera angles.

---

## Getting Started

### Prerequisites
* Python 3.9+
* PyTorch (CUDA enabled recommended)
* OpenCV, NumPy, Matplotlib

### Installation
git clone [https://github.com/AKDev32/HelmetDector.git](https://github.com/AKDev32/HelmetDector.git)
cd HelmetDector
pip install -r requirements.txt


---

## Educational Objectives

Through the development of this project, I have conducted empirical investigations into:

* **Transfer Learning Strategies**: Systematically fine-tuning a pre-trained convolutional backbone (e.g., CSPDarknet) on a niche safety dataset to achieve high precision despite limited labeled data.
* **Hyperparameter Optimization**: Analyzing the correlation between **Batch Size** and **Learning Rate** on the convergence of the object detection loss function (specifically CIoU/DIoU loss).
* **Deployment Constraints**: Critically balancing the trade-off between model depth (Mean Average Precision) and computational efficiency (Frames Per Second) for edge-case hardware.

---

## Future Work

To evolve this system into a production-ready safety suite, the following roadmap is proposed:

1.  **Optical Character Recognition (OCR)**: Integration of a text-recognition module to extract license plate data or worker IDs during safety violations.
2.  **Temporal Consistency with DeepSORT**: Implementation of multi-object tracking (MOT) to ensure persistent identification of individuals across frames and prevent redundant violation logging.
3.  **Hardware Acceleration**: Exporting the model weights to **TensorRT** or **ONNX** formats to facilitate ultra-low latency inference on NVIDIA Jetson or other embedded AI platforms.

---

**Author:** [Aman Kumar/ AKDev32]  
**Academic Focus:** Computer Vision / Applied Deep Learning
