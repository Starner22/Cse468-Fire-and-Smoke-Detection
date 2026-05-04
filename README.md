Fire & Smoke Detection System
A real time fire and smoke detection system using YOLOv8 model.
The model is trained on multiple merged datasets and is capable of detecting both large fires and small flame sources in real time.

Table of Contents
Overview
Features
Repository Structure
Model Details
Datasets
Methodology
Performance Metrics
Limitations
Future Works
Authors

Overview
Fire is a fatal hazard if not contained at its early stages. This project aims to build a early warning system and explores building a robust detector by fine tuning Rolov8n and Yolov8s on a large, diverse dataset, containing both small and large indoor, outdoor and wildfires. This project also aims to look into it detection performance, limitations, and behavior under different scenarios

Features
  * Real-time fire detection using webcam or video input
  * Detection of small flame sources (candle, lighter, etc)
  * Partial smoke detection (dependent on visibility conditions)
  * Reduced false positives compared to baseline training
  * Works on live feed, pre-recorded video and static images

Repository Structure
Cse468-Fire-and-Smoke-Detection/
-> data/
    -> Dataset link.txt
-> others/
    -> FINAL GROUP REPORT.pdf
    -> Final slides (G7).pptx
    -> Video Demo.mp4
    -> update report (Khatune Jannat).pdf
    -> update report (Mahdin Muhammad Jakir).pdf
-> support/
    -> Yolov8n weights/
        -> best.pt
        -> last.pt
      -> Yolov8s weights/
        -> best.pt
        -> last.pt
      -> Dataset_Merger.ipynb
-> README.md
-> main.ipynb
-> requirements.txt

Model Details
* Model: YOLOv8
* Goal: Object Detection
* Classes: fire, smoke

Datasets
Source - Type
D-Fire- Outdoor + Indoor
Indoor - Indoor
Flame-BD - Small fire
Iron Wolf- Wildfire+ Indoor

A total of 45,252 images

Methodology
Model used: YOlov8s and YOlov8n
1. Data Preparation
   A variation of indoor, outdoor, small and big fire and smoke images, along with false positive images were collected from roboflow and kaggle, and merged.
   The dataset is standardized into YOLO format, keeping class labels constant throughout:
   0 - fire
   1- smoke
   Data was cleaned, removing any images without label.txt
2. Hyperparameter Tuning and Training
   imgsz=736, batch=32, amp=True, epoch = 45, optimizer = auto
3. Evaluation
   Metrics used:
   * Precision
   * Recall
   * mAP50
   * mAP50–95
   External evaluation
   * Tested on unseen datasets
  
Performance Metrics
Model - Parameters - Epochs - mAP50 - Precision- Recall- mAP50-95
Yolov8n- 3.2M - 45 - 80.0% - 81.3% - 71.8%
Yolov8s- 11.2M - 45- 81.8%- 81.6% - 74.8%

Limitations
* Dataset bias toward visible, well-defined fire instances
* Limited representation of thin or early-stage smoke
* Model not yet convergedyet. Both models were stopped at 45 epochs due to compute constraints.

Future Work
* Complete training to 100 epochs with access to higher-compute GPU
* Explore YOLOv8m for higher accuracy if compute allows
* Gather more smoke-heavy datasets
* Quantize the model to make it run on mobile and edge devices

Credentials

Authors
Name- GitHub
Mahdin Muhammad Jakir - @Starner22
Khatune Jannat   -      @hridikatuly100

Course: Cse468 Computer Vision
Institution: North South University
Supervisor: Dr. Mohammad Shifat-E-Rabbi [MSRb]
Semester: Spring 2026
