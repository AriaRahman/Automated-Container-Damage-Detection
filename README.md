Overview
This project implements an automated container damage detection system using the RF-DETR (Roboflow Detection Transformer) model. The system identifies three types of container damages: dent, hole, and rust, leveraging transformer-based architecture for high accuracy and efficiency.
The pipeline consists of:

Data Collection
Dataset Annotation & Preprocessing
Model Training with RF-DETR
Model Evaluation & Performance Analysis


Dataset

Source: https://roboflow.com
Size: 5,761 images of shipping containers
Classes: dent, hole, rust
Format: COCO for compatibility with deep learning frameworks


Data Preprocessing
To ensure consistency:

Auto-Orient: Correct image orientation using EXIF metadata
Resize: All images resized to 640 × 640 pixels


Data Augmentation

Split: 70% training, 20% validation, 10% testing
Strategies:

Horizontal flip
Brightness adjustment (-20% to +20%)
Rotation (-15° to +15°)



After augmentation:

Total Images: 9,652

Training: 6,740
Validation: 1,929
Testing: 983




Model Architecture: RF-DETR

Base: DETR by Facebook AI Research
Enhancements:

Deformable attention for multi-scale feature capture
Transformer backbone with DINOv2
Eliminates region proposals, anchor boxes, and NMS


Performance:

mAP: 60.5 on MS COCO
Speed: 25 FPS




Experimental Setup

Environment: Google Colab Pro
Hardware: NVIDIA A100-SXM4 GPU (80GB VRAM)
Software:

Python 3.12
CUDA 12.4
rfdetr==1.2.1, supervision==0.26.1, roboflow


Batch Size: 16
Gradient Accumulation: 1


Results
Per-Class Metrics








































ClassmAP[50:95]mAP[50]PrecisionRecallDent0.6840.9520.9840.84Rust0.6350.9350.9720.84Hole0.5860.8570.9110.84All0.6350.9140.9550.84
Comparison with Other Models









































ModelAccuracyPrecisionRecallYOLO-NAS0.9120.9240.8675YOLOv80.6360.8510.72YOLOv110.8190.9190.761YOLOv120.8190.7890.784RF-DETR0.940.920.90

Visualizations

Training vs Validation Loss & Accuracy
Precision, Recall, and mAP curves across epochs
Sample detections of container damages


Conclusion
The RF-DETR model demonstrates superior performance in detecting container damages compared to YOLO-based models, achieving:

Accuracy: 94%
Precision: 92%
Recall: 90%

This approach improves inspection reliability and speed, reducing manual errors and enhancing operational safety in port logistics.

Future Work

Hyperparameter optimization
Model compression for real-time inference
Scaling to larger variants for improved accuracy

