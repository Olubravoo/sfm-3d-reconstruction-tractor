# sfm-3d-reconstruction-tractor
A Computer Vision pipeline for 3D Sparse Reconstruction from stop-motion photography. Implemented using Python, OpenCV, and Essential Matrix estimation to recover camera pose and generate 3D point clouds from 2D images.
### 3D Sparse Reconstruction from Stop-Motion Datasets

[Project Demo](your_tractor_3D_v2.gif)

## Project Overview
This repository contains a Computer Vision pipeline developed to reconstruct a 3D scene from a "stop-motion" image sequence. The primary challenge was processing a dataset of 279 images with low temporal continuity. By utilizing **Structure from Motion (SfM)** principles, the pipeline successfully recovers camera trajectory and generates a 3D sparse point cloud of a LEGO tractor.

## Tech Stack & Environment
- **Language:** Python 3.x
- **Environment:** Jupyter Notebook (Optimized for macOS)
- **Core Libraries:** OpenCV, NumPy, Matplotlib, TensorFlow (for data tensors)
- **Techniques:** ORB Feature Matching, Essential Matrix Estimation, RANSAC, Dense Optical Flow (Farneback).


### 1. Robust Feature Matching
Implemented **ORB (Oriented FAST and Rotated BRIEF)** to detect stable landmarks. Because the images were taken in a "stop-motion" style, the pipeline uses a high RANSAC threshold to filter out geometric outliers caused by the jumpy camera movement.

### 2. Motion Interpolation
To address the "Temporal Discontinuity" of the stop-motion frames, I applied **Dense Optical Flow**. This technique calculates velocity vectors for every pixel, allowing for smoother motion estimation and aiding in the recovery of the camera's translation ($t$) and rotation ($R$).

### 3. Pose Recovery & Triangulation
The pipeline solves for the **Essential Matrix** to map the camera's path through the dining table scene. The final output is a 3D sparse point cloud, visualized through Matplotlib's 3D projection tools.

##  Repository Structure
- `sfm_reconstruction.ipynb`: Main project notebook containing the end-to-end pipeline.
- `tractor_preview.gif`: Animated result showing the camera walkthrough.
- `images/`: (Optional) Sample images from the 279-frame sequence.

##  Summary of Results
The project successfully demonstrated that even with non-continuous source data, accurate spatial geometry can be recovered. The resulting point cloud clearly defines the structure of the LEGO model and the supporting surface, confirming the effectiveness of the RANSAC-filtered SfM approach.

---
