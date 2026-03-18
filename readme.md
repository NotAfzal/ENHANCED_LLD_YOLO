# LLD-YOLO: Lightweight Low-Light Object Detection on ExDark

This repository presents an implementation of **LLD-YOLO**, a lightweight YOLO-based model designed specifically for **object detection in low-light environments** using the **ExDark dataset**.  

The project includes modular model components, training and evaluation pipelines, improved architectural variants, and visual results for performance analysis.

---

## Repository Structure
- **config.py** — Configuration for experiments  
- **run.py / run_improved.py** — Training scripts  
- **compare_models.py** — Script to compare model performance  
- **paper_table.py** — Generates formatted result tables  
- **evaluate.py** — Evaluation pipeline  
- **data/** — Dataset loading, annotation parsing, augmentations  
- **models/** — Backbones, enhancement modules, detection heads  
- **train/** — Loss functions, metrics, training logic  
- **weights/** — Saved model weights  
- **results/** — Outputs, logs, and visualizations  

---

## ExDark Dataset Overview

The **ExDark (Extreme Low-Light Dataset)** consists of images captured in challenging lighting conditions.

### Key Characteristics
- 7,363 low-light images  
- 12 object classes (e.g., Car, Dog, Bottle, People)  
- Real-world night and dim-light environments  
- High noise, low contrast, and shadows  

### Dataset Format
- Images: `data/ExDark/images/`  
- Labels: `data/ExDark/labels/`  

### Preprocessing Techniques
- Gamma correction  
- CLAHE (contrast enhancement)  
- Normalization  
- Geometric augmentations (rotation, scaling)  
- Noise-aware transformations  

---

## Model Architecture

### Original LLD-YOLO
- Lightweight backbone network  
- Basic feature fusion strategy  
- Standard YOLO detection head  

### Improved LLD-YOLO
- Low-Light Enhancement Module (LL-EM)  
- Enhanced backbone with improved convolution blocks  
- Optional modules like DBB / Ghost / ELAN  
- Improved bounding box loss (CIoU/EIoU)  

### Design Goals
- Improve feature extraction in low-light conditions  
- Maintain fast inference speed  
- Ensure stable and efficient training  

---

## Results on ExDark

### Performance Metrics

| Model                 | mAP@50 | mAP@50-95 | Precision | Recall | F1-score | FPS  | Latency (ms) |
|-----------------------|--------|-----------|-----------|--------|----------|------|---------------|
| Original LLD-YOLO     | 0.423  | 0.219     | 0.61      | 0.54   | 0.57     | 42.7 | 23.4          |
| Improved LLD-YOLO     | 0.487  | 0.261     | 0.67      | 0.59   | 0.62     | 45.1 | 21.3          |

The improved model achieves noticeable gains in detection accuracy while maintaining real-time performance.

---

## Visualizations

### Precision–Recall Curve
![PR Curve](https://github.com/NotAfzal/ENHANCED_LLD_YOLO/raw/main/results/figures/pr_curve.png)

### Loss Curves
![Loss Curves](https://github.com/NotAfzal/ENHANCED_LLD_YOLO/raw/main/results/figures/loss_curves.png)

### Metrics Comparison
![Metrics Barplot](https://github.com/NotAfzal/ENHANCED_LLD_YOLO/raw/main/results/figures/metrics_barplot.png)

### Confusion Matrices

#### Original Model
![Confusion Matrix - Original](https://github.com/NotAfzal/ENHANCED_LLD_YOLO/raw/main/results/figures/confusion_original.png)

#### Improved Model
![Confusion Matrix - Improved](https://github.com/NotAfzal/ENHANCED_LLD_YOLO/raw/main/results/figures/confusion_improved.png)

---

## Key Observations

### Detection Performance
- Improved feature extraction in low-light scenarios  
- Better handling of noise and poor illumination  
- More accurate bounding box predictions  

### Training Behavior
- Faster convergence  
- More stable loss trends  
- Reduced fluctuations during training  

### Efficiency
- Improved FPS (42.7 → 45.1)  
- Reduced latency (23.4 ms → 21.3 ms)  

---

## Summary

LLD-YOLO focuses on enhancing object detection performance under low-light conditions by combining efficient architecture design with illumination-aware modules. The improved version demonstrates better accuracy, stability, and speed, making it suitable for real-time applications in challenging environments.

---

## Authors
- Afzal Asim  
- Samadrito Chakraborty
