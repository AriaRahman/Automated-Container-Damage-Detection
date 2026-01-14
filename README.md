
<h1 align="center"> Container Damage Detection using RF-DETR</h1>

## Overview
This project implements an automated **container damage detection system** using the **RF-DETR (Roboflow Detection Transformer)** model.  
The system identifies three types of container damages: **Dent**, **Hole**, and **Rust**, leveraging transformer-based architecture for high accuracy and efficiency.

The pipeline consists of:
1. **Data Collection**
2. **Dataset Annotation & Preprocessing**
3. **Model Training with RF-DETR**
4. **Model Evaluation & Performance Analysis**

---

<h2>Dataset</h2>
- **Source:** https://roboflow.com  
- **Size:** 5,761 images of shipping containers  
- **Classes:** `dent`, `hole`, `rust`  
- **Format:** COCO for compatibility with deep learning frameworks  

---

<h2> Data Preprocessing</h2>
To ensure consistency:
- **Auto-Orient:** Correct image orientation using EXIF metadata  
- **Resize:** All images resized to `640 × 640` pixels  

---

<h2> Data Augmentation</h2>
- **Split:** `70%` training, `20%` validation, `10%` testing  
- **Strategies:**  
  - Horizontal flip  
  - Brightness adjustment (-20% to +20%)  
  - Rotation (-15° to +15°)  

After augmentation:
- **Total Images:** 9,652  
  - Training: 6,740  
  - Validation: 1,929  
  - Testing: 983  

---

<h2> Model Architecture: RF-DETR</h2>
- **Base:** DETR by Facebook AI Research  
- **Enhancements:**  
  - Deformable attention for multi-scale feature capture  
  - Transformer backbone with **DINOv2**  
  - Eliminates region proposals, anchor boxes, and NMS  
- **Performance:**  
  - mAP: `60.5` on MS COCO  
  - Speed: `25 FPS`  

---

<h2> Experimental Setup</h2>
- **Environment:** Google Colab Pro  
- **Hardware:** NVIDIA A100-SXM4 GPU (80GB VRAM)  
- **Software:**  
  - Python 3.12  
  - CUDA 12.4  
  - `rfdetr==1.2.1`, `supervision==0.26.1`, `roboflow`  
- **Batch Size:** 16  
- **Gradient Accumulation:** 1  

---

<h2>Results</h2>
### Per-Class Metrics
| Class | mAP[50:95] | mAP[50] | Precision | Recall |
|-------|-----------|---------|-----------|--------|
| Dent  | 0.684     | 0.952   | 0.984     | 0.84   |
| Rust  | 0.635     | 0.935   | 0.972     | 0.84   |
| Hole  | 0.586     | 0.857   | 0.911     | 0.84   |
| **All** | 0.635   | 0.914   | 0.955     | 0.84   |

### Comparison with Other Models
| Model       | Accuracy | Precision | Recall |
|-------------|----------|-----------|--------|
| YOLO-NAS    | 0.912    | 0.924     | 0.8675 |
| YOLOv8      | 0.636    | 0.851     | 0.72   |
| YOLOv11     | 0.819    | 0.919     | 0.761  |
| YOLOv12     | 0.819    | 0.789     | 0.784  |
| **RF-DETR** | **0.94** | **0.92**  | **0.90**|

---

<h2>Conclusion</h2>
The RF-DETR model demonstrates superior performance in detecting container damages compared to YOLO-based models, achieving:
- **Accuracy:** 94%  
- **Precision:** 92%  
- **Recall:** 90%  

This approach improves inspection reliability and speed, reducing manual errors and enhancing operational safety in port logistics.

---

<h2>Future Work</h2>
- Hyperparameter optimization  
- Model compression for real-time inference  
- Scaling to larger variants for improved accuracy  

---

<h2>How to Run</h2>
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/container-damage-detection.git

