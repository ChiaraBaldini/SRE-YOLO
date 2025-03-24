# SRE-YOLO: Super-Resolution Enhanched YOLO for real-time laryngeal lesion detection
## Overview
This project focuses on the development and implementation of SRE-YOLO, a DL model designed to assist less-experienced medical personnel in the real-time detection of laryngeal lesions from endoscopic White Light (WL) and Narrow-Band Imaging (NBI) images. Traditional diagnostic approaches rely heavily on endoscopic examination, which requires expert interpretation and may be limited by subjective assessment.

To address these challenges, this approach integrates a YOLOv8 nano (YOLOv8n) baseline with a Super-Resolution (SR) branch during training to enhance lesion detection. The SR component is decoupled during inference to maintain the low computational demand of the YOLOv8n baseline. The proposed method was evaluated on a multi-center dataset encompassing diverse laryngeal pathologies and imaging modalities, demonstrating a 5% improvement in Average Precision (AP@IoU=0.5) in lesion detection compared to the YOLOv8n baseline while maintaining an inference speed of 58.8 Frames Per Second (FPS). 

<img src="imgs\YOLOsr_diagram_with_modules (1).jpg" alt="Example Image" width="400"/>

## Results

| Method | **mAP50** | **FPS** | **GFLOPs** |
|:---:|:---:|:---:|:---:|
| **YOLOv8**  |0.77|8.2|58.8|
| **SRE-YOLO** | **0.82** 🚀 | 8.2 | 58.8|



## Table of Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [Authors](#authors)
- [License](#license)
- [Acknowledgments](#acknowledgments)
- [Citation](#citation)

## Introduction
SRE-YOLO employs the nano version of YOLOv8 to detect lesion from input data. During training, features extracted at different level of the YOLO backbone were combined and augmented with the SR branch, which is based on the EDSR architecture. In the inference phase, SRE-YOLOm maintains the inference speed of the YOLOv8n baseline, i.e., 58.8 Frames Per Second (FPS) on a 48 GB NVIDIA RTX A6000 GPU, by decoupling the SR branch. the proposed method was evaluated, both internally and externally, on multi-center datasets encompassing diverse laryngeal pathologies and endoscopic imaging modalities. Comparative analyses against state-of-the-art deep learning methods highlighted the potential of SRE-YOLO in developing efficient DL-driven decision support systems for real-time detection of laryngeal lesions across different acquisition settings without increasing computational demands.

If you want to use the SRE-YOLO-related datasets for research purposes, please fill and return the following [DataRequestForm]().

## Installation

Steps to install the project locally (system requirements, necessary packages, and configuration instructions).

```bash
# Clone the repository
git clone https://github.com/ChiaraBaldini/SRE-YOLO.git

# Navigate to the project directory
cd SRE-YOLO

### Dependencies
- Python 3.8+
- PyTorch 1.8+
- CUDA (for NVIDIA GPU support)

# Install dependencies (code  based on Ultralytics v8.0.192)
pip install -r requirements.txt
```

## Usage
```
### Executing program
import ultralytics
from ultralytics import YOLO

model = YOLO("yolov8n.yaml")

model.train(data='<your_dataset>.yaml', epochs=150, patience=50, imgsz=640, sr=True)
```
When ```sr=True```, the additional SR branch is activated. You can also adjust the weight of the SR loss in *ultralytics/nn/task.py*. By default, it is set to 0.1.

## Authors
Contributors names and contact info
For inquiries related to the paper, dataset or code, please contact:
- Chiara Baldini , [chiara.baldini@iit.it]

## Acknowledgments
* This code is built on the [YOLOv8 GitHub repository](https://github.com/ultralytics/ultralytics).
* The SR branch was implemented by adapting the version of [Zhang et al.](https://github.com/icey-zhang/SuperYOLO) to YOLOv8, as in [YOLOSR-WeaponDetection
](https://github.com/daniebera/YOLOSR-WeaponDetection).
* We thank the authors for sharing the codes.

## Citation
If our code is helpful to you, please cite:

```
@article{BALDINI2025108539,
title = {Improving real-time detection of laryngeal lesions in endoscopic images using a decoupled super-resolution enhanced YOLO},
author = {Chiara Baldini and Lucia Migliorelli and Daniele Berardini and Muhammad Adeel Azam and Claudio Sampieri and Alessandro Ioppi and Rakesh Srivastava and Giorgio Peretti and Leonardo S. Mattos},
journal = {Computer Methods and Programs in Biomedicine},
volume = {260},
pages = {108539},
year = {2025},
issn = {0169-2607},
doi = {https://doi.org/10.1016/j.cmpb.2024.108539},
url = {https://www.sciencedirect.com/science/article/pii/S0169260724005327}
}
```
