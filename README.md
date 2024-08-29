# SRE-YOLO: Super-Resolution Enhanched YOLO for real-time laryngeal lesion detection
## Overview
This project focuses on the development and implementation of SRE-YOLO, a DL model designed to assist less-experienced medical personnel in the real-time detection of laryngeal lesions from endoscopic White Light (WL) and Narrow-Band Imaging (NBI) images. Traditional diagnostic approaches rely heavily on endoscopic examination, which requires expert interpretation and may be limited by subjective assessment. To address these challenges, this approach integrates a YOLOv8 nano (YOLOv8n) baseline with a Super-Resolution (SR) branch during training to enhance lesion detection. The SR component is decoupled during inference to maintain the low computational demand of the YOLOv8n baseline. The proposed method was evaluated on a multi-center dataset encompassing diverse laryngeal pathologies and imaging modalities, demonstrating a 5% improvement in Average Precision (AP@IoU=0.5) in lesion detection compared to the YOLOv8n baseline while maintaining an inference speed of 58.8 Frames Per Second (FPS). 

**Note:** The codebase will be made available here after the paper is accepted for publication in Computer Methods and Programs in Biomedicine.

## Table of Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [Authors](#authors)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Introduction
SRE-YOLO employs the nano version of YOLOv8 to detect lesion from input data. During training, features extracted at different level of the YOLO backbone were combined and augmented with the SR branch, which is based on the EDSR architecture. In the inference phase, SRE-YOLOm maintains the inference speed of the YOLOv8n baseline, i.e., 58.8 Frames Per Second (FPS) on a 48 GB NVIDIA RTX A6000 GPU, by decoupling the SR branch. the proposed method was evaluated, both internally and externally, on multi-center datasets encompassing diverse laryngeal pathologies and endoscopic imaging modalities. Comparative analyses against state-of-the-art deep learning methods highlighted the potential of SRE-YOLO in developing efficient DL-driven decision support systems for real-time detection of laryngeal lesions across different acquisition settings without increasing computational demands.

Diagrams will be included upon paper acceptance.

If you want to use the SRE-YOLO-related datasets for research purposes, please fill and return the following [DataRequestForm]().

## Installation

Steps to install the project locally. Include system requirements, necessary packages, and configuration instructions.

```bash
# Clone the repository
git clone https://github.com/your-username/project-name.git

# Navigate to the project directory
cd project-name

# Install dependencies
npm install  # or pip install -r requirements.txt for Python, etc.

# Start the application
npm start    # or python app.py, etc.
## Description

An in-depth paragraph about your project and overview of use.

## Getting Started

### Dependencies

* Describe any prerequisites, libraries, OS version, etc., needed before installing program.
* ex. Windows 10

### Installing

* How/where to download your program
* Any modifications needed to be made to files/folders

```

## Usage
```
### Executing program

* How to run the program
* Step-by-step bullets
```

## Authors
Contributors names and contact info
For inquiries related to the paper, dataset or code, please contact:
- Chiara Baldini  , [chiara.baldini@iit.it]

## Acknowledgments
* This code is built on the [YOLOv8 GitHub repository](https://github.com/ultralytics/ultralytics).
* The SR branch was implemented by adapting the version of [Zhang et al.](https://github.com/icey-zhang/SuperYOLO) to YOLOv8.
