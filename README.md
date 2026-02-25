# Endoscopic 3D Reconstruction and Coverage Analysis

Official code for "3D Reconstruction of the Colon Surface from Monocular Endoscopy for Missing Regions Quantification". This repository provides a complete pipeline for **3D reconstruction** from endoscopic sequences and **advanced mesh coverage analysis**. It integrates depth estimation, camera pose tracking, and a specialized module to quantify and visualize areas of the anatomy that were missed during the procedure.

---

## 📂 Repository Structure

The project is organized into four main modules:

* **`Depth_estimation/`**: Contains the Deep Learning models and scripts to predict depth maps from endoscopic frames.
* **`Pose_estimation/`**: Includes algorithms to estimate the camera trajectory (Rotation/Translation) across the sequence.
* **`3D_reconstruction/`**: Features the `reconstruction.py` script, which uses a **Scalable TSDF** (Truncated Signed Distance Function) Volume to fuse depth and pose data into a high-fidelity 3D mesh.
* **`Missing_regions/`**: Features the `missing.py` script. This module performs **Poisson Surface Reconstruction** to identify "holes" in the geometry, mapping and quantifying unobserved regions.

---
## 🛰️ Workflow Pipeline

<p align="center">
  <img src="https://github.com/user-attachments/assets/224ed15b-4fb2-423d-b6cf-284c182a9d45" width="60%">
</p>

---

## 📊 Dataset Validation

The pipeline has been tested and validated on two major benchmark datasets:

1.  **C3VD**: A high-fidelity clinical dataset providing ground truth for depth and camera pose.
2.  **SimCol3D**: A synthetic colonoscopy dataset ideal for testing reconstruction robustness.

---

## ⚙️ Data Organization

To ensure the `reconstruction.py` script to work correctly, organize your data as follows:

```plaintext
/data
  ├── sequence_name                 
  │   ├── Frames/                     # Input RGB frames
  │   ├── Depth/                      # Predicted depth maps (.png or .tiff)
  │   ├── SavedPosition.txt           # Camera positions (X, Y, Z)
  │   ├── SavedRotationQuaternion.txt # Camera rotations (Quaternions)
  │   ├── cam.txt                     # Camera intrinsics (matrix format)
```

## TSDF 3D Reconstruction 

<p align="center">
  <img src="LINK_DELLA_TUA_GIF" width="50%" alt="3D Reconstruction Demo">
  <br>
  <i>Progressive 3D Reconstruction using Scalable TSDF Volume.</i>
</p>


