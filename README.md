# Fire & Smoke Detection System

A real-time fire and smoke detection system using YOLOv8.
The model is trained on multiple merged datasets and detects both large fires and small flame sources in real time.

---

## Table of Contents

* [Overview](#overview)
* [Features](#features)
* [Repository Structure](#repository-structure)
* [Model Details](#model-details)
* [Datasets](#datasets)
* [Methodology](#methodology)
* [Performance Metrics](#performance-metrics)
* [Limitations](#limitations)
* [Future Work](#future-work)
* [Authors](#authors)

---

## Overview

Fire is a critical hazard if not detected at an early stage. This project focuses on building an early warning system by fine-tuning YOLOv8n and YOLOv8s on a large and diverse dataset. The dataset includes indoor, outdoor, small-scale, and wildfire scenarios.

The project evaluates:

* detection performance
* generalization ability
* behavior under different environmental conditions

---

## Features

* Real-time fire detection using webcam or video input
* Detection of small flame sources (candle, lighter, etc.)
* Partial smoke detection (dependent on visibility conditions)
* Reduced false positives compared to baseline training
* Works on live feed, pre-recorded video, and static images

---

## Repository Structure

```text
Cse468-Fire-and-Smoke-Detection/
├── data/
│   └── Dataset link.txt
├── others/
│   ├── FINAL GROUP REPORT.pdf
│   ├── Final slides (G7).pptx
│   ├── Video Demo.mp4
│   ├── update report (Khatune Jannat).pdf
│   └── update report (Mahdin Muhammad Jakir).pdf
├── support/
│   ├── Yolov8n weights/
│   │   ├── best.pt
│   │   └── last.pt
│   ├── Yolov8s weights/
│   │   ├── best.pt
│   │   └── last.pt
│   └── Dataset_Merger.ipynb
├── main.ipynb
├── requirements.txt
└── README.md
```

---

## Model Details

* Model: YOLOv8 (Ultralytics)
* Task: Object Detection
* Classes:

  * `fire`
  * `smoke`

---

## Datasets

| Dataset           | Type              | Link                                                                                 |
| ----------------- | ----------------- | ------------------------------------------------------------------------------------ |
| D-Fire            | Indoor + Outdoor  | https://github.com/gaia-solutions-on-demand/DFireDataset                             |
| Indoor Fire Smoke | Indoor            | https://universe.roboflow.com/object-detection-7qn6l/indoor-fire-smoke               |
| Flame-BD          | Small Fire        | https://universe.roboflow.com/flame-bd9xu/fire-detection-gvj54                       |
| IronWolf          | Wildfire + Indoor | https://www.kaggle.com/datasets/ironwolf437/fire-detection-dataset?resource=download |

**Total images:** 45,252

---

## Methodology

### Model Used

* YOLOv8n
* YOLOv8s

### 1. Data Preparation

A diverse dataset was constructed by merging multiple sources containing:

* indoor and outdoor fire scenarios
* small and large fires
* smoke samples
* false positive samples

The dataset was converted to YOLO format with consistent labels:

* `0 → fire`
* `1 → smoke`

Cleaning steps:

* removed images without corresponding label files
* ensured label consistency

---

### 2. Training Configuration

* Image size: 736
* Batch size: 32
* Epochs: 45
* Mixed precision: Enabled
* Optimizer: Auto

---

### 3. Evaluation

Metrics used:

* Precision
* Recall
* mAP50
* mAP50–95

External evaluation:

* tested on unseen datasets to assess generalization

---

## Performance Metrics

| Model   | Parameters | Epochs | mAP50 | Precision | Recall | mAP50-95 |
| ------- | ---------- | ------ | ----- | --------- | ------ | -------- |
| YOLOv8n | 3.2M       | 45     | 80.0% | 81.3%     | 71.8%  | —        |
| YOLOv8s | 11.2M      | 45     | 81.8% | 81.6%     | 74.8%  | —        |

---

## Limitations

* Dataset bias toward visible fire instances
* Limited representation of early-stage or thin smoke
* Models stopped at 45 epochs due to compute constraints
* Not fully converged

---

## Future Work

* Extend training to 100 epochs with better compute
* Experiment with YOLOv8m for improved accuracy
* Collect more smoke-focused datasets
* Apply model quantization for edge deployment

---

## Authors

| Name                  | GitHub                            |
| --------------------- | --------------------------------- |
| Mahdin Muhammad Jakir | https://github.com/Starner22      |
| Khatune Jannat        | https://github.com/hridikatuly100 |

---

**Course:** CSE468 – Computer Vision
**Institution:** North South University
**Supervisor:** Dr. Mohammad Shifat-E-Rabbi (MSRb)
**Semester:** Spring 2026

---
