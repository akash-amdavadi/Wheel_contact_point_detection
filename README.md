# Wheel Contact Point Detection (YOLOv8 Pose)

Monocular, keypoint-based detection of **wheel–ground contact points** from fixed cameras using **YOLOv8 Pose**. The system targets downstream tasks such as estimating inter-vehicle spacing **without explicit camera calibration**.

**Authors:** Akash Mahendrabhai Amdavadi,  Vatsal Anand Pande
**Affiliation:** Maschinenbau und Verfahrenstechnik, RPTU Kaiserslautern-Landau, Germany

---

## Overview

This project trains and deploys a YOLOv8 pose model to detect wheel–ground contact points in road traffic scenes. Video frames were captured with a **GoPro Hero5** mounted on a **stationary pole (~3–4 m)**, under **varied lighting conditions** (day/evening/night). The dataset is **custom-labeled** at precise wheel contact locations (not generic wheel centers).

**Key characteristics**
- Develop a **YOLOv8 Pose–based** model to detect **wheel–road contact keypoints** from a single, stationary **monocular** camera.  
- Enable **approximate spacing/distance estimation** between vehicles **without explicit camera calibration**.  
- Achieve **robustness across lighting conditions** (day/evening/night) and common traffic scenarios.  
- Lightweight repository: **no raw images/labels or runs** committed; only `dataset/data.yaml` documents structure

---

## Goals and Scope

**Goals**
- Detect per-vehicle wheel contact keypoints using YOLOv8 Pose
- Be robust across common lighting and traffic scenarios
- Provide a practical starting point for spacing/distance estimation from monocular footage

## Scope
- Designed for **traffic monitoring and analysis** using a single stationary monocular camera.  
- Provides a **baseline method** for detecting wheel–road contact points and approximating inter-vehicle spacing.  
- Useful as a foundation for **research and academic projects** in intelligent transportation and computer vision.  
- Not intended as a production-ready system — dataset size (~1150 images) and model performance highlight the need for further expansion, augmentation, and tuning.  


---

## Dataset
- **Size:** ~1,150 labeled frames (1920×1080 @ 24 FPS) captured with a **GoPro Hero5**.  
- **Setup:** Stationary **monocular** camera ~3–4 m above the roadway.  
- **Conditions:** Day / evening / night; diverse vehicle types and occlusions.  
- **Annotation:** **Roboflow** Precise **wheel–road contact keypoints** (2–4+ per vehicle) created in Roboflow; exported in **YOLOv8 pose** format.  
- **Split:** ~70% train / 20% val / 10% test.  
  

> In this repository, only **`dataset/data.yaml`** is tracked.  
> Folders like `dataset/images/` and `dataset/labels/` are **ignored** via `.gitignore`.

---

## Methodology

### Model
- **Base:** `yolov8n-pose` (YOLOv8 pose, nano variant for resource-constrained training)
- **Input size:** high-resolution training to preserve small keypoint detail
- **Augmentation (baseline):** minimal/none; focus on real-world frames
- **Hardware:** mixed environments (GPU and CPU-only)

### Inference Pipeline (high level)
1. Load trained YOLOv8 pose weights
2. Run prediction on images or video streams

---

## Future Work
- Expand the custom dataset (more vehicles, viewpoints, and lighting/weather) to improve generalization.
- Use targeted data augmentation (brightness/contrast, noise/blur, flips/rotations, scale/crop) to bring variation into the dataset.
- Tune training parameters (image size, batch size, epochs, learning rate, augmentation strength) for better precision/recall.





