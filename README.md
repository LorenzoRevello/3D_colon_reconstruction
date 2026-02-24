# 3D_colon_reconstruction
Official code for "3D Reconstruction of the Colon Surface from Monocular Endoscopy for Missing Regions Quantification". This pipeline uses TSDF fusion and Poisson reconstruction to explicitly identify, map, and quantify unobserved mucosa (blind spots) from standard monocular videos, enabling objective colonoscopy quality assessment.

# Endoscopic 3D Reconstruction and Coverage Analysis

This repository provides a complete pipeline for **3D reconstruction** from endoscopic sequences and **advanced mesh coverage analysis**. It integrates depth estimation, camera pose tracking, and a specialized module to quantify and visualize areas of the anatomy that were missed during the procedure.

---

## 📂 Repository Structure

The project is organized into four main modules:

* **`depth_estimation/`**: Contains the Deep Learning models and scripts to predict depth maps from endoscopic frames.
* **`pose_estimation/`**: Includes algorithms to estimate the camera trajectory (Rotation/Translation) across the sequence.
* **`3D_reconstruction/`**: Features the `reconstruction.py` script, which uses a **Scalable TSDF** (Truncated Signed Distance Function) Volume to fuse depth and pose data into a high-fidelity 3D mesh.
* **`MISSING_Region/`**: Features the `close_mesh_poisson.py` script. This module performs **Poisson Surface Reconstruction** to identify "holes" in the geometry, mapping and quantifying unobserved regions.

---

## 📊 Dataset Validation

The pipeline has been tested and validated on two major benchmark datasets:

1.  **C3VD**: A high-fidelity clinical dataset providing ground truth for depth and camera pose.
2.  **SimCol3D**: A synthetic colonoscopy dataset ideal for testing reconstruction robustness.

---

## ⚙️ Data Organization

To ensure the scripts work correctly, organize your data as follows:

```plaintext
/data
  ├── sequence_name
  │   ├── Frames_metric/              # Predicted depth maps (.png) and/or RGB frames
  │   ├── SavedPosition.txt           # Camera positions (X, Y, Z)
  │   ├── SavedRotationQuaternion.txt # Camera rotations (Quaternions)
  │   ├── cam.txt                     # Camera intrinsics (matrix format)
  │   └── mesh.ply                    # (Output) The generated 3D reconstruction
