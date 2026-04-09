# 🌕 Lunar Crater Detection using Chandrayaan-2 Imagery

This repository presents an end-to-end pipeline for detecting lunar craters using high-resolution imagery captured by ISRO's **Chandrayaan-2** mission. The system leverages the **Ultralytics YOLO11** object detection framework, enhanced with custom backbone architectures from the [Timm](https://github.com/huggingface/pytorch-image-models) library.

---

## 📌 Project Overview

This project addresses the challenge of automated lunar crater detection—a critical task for planetary mapping, surface age estimation, and mission planning. Using imagery from Chandrayaan-2's Orbiter High Resolution Camera (OHRC) and Terrain Mapping Camera-2 (TMC-2), we developed a YOLO11-based detection model with custom ResNet101 backbone optimized for lunar surface features.

**Key Objectives:**
- Detect craters of varying sizes in high-resolution lunar imagery
- Implement and evaluate YOLO11 architecture for planetary surface analysis
- Evaluate model generalization across datasets with different resolutions and characteristics

---

## 🛰️ Datasets

The project uses two distinct datasets from Chandrayaan-2:

| Camera | Resolution | Tile Sizes | Characteristics |
|--------|------------|------------|-----------------|
| **OHRC** | ~0.25 m/pixel | 304×640 px | Very high resolution, detailed surface features |
| **TMC-2** | ~5 m/pixel | 79×640 px | Lower resolution, broader coverage |

**Data Preparation:**
- Images tiled and preprocessed to maintain aspect ratio
- Bounding box annotations created manually using **Roboflow**
- Datasets formatted for YOLO training pipeline compatibility
- Stored in `resourses/folderohr/` (OHRC dataset) and `resourses/foldertmc/` (TMC-2 dataset)

---

## 🧠 Model Architecture

The detection system is built on the **Ultralytics YOLO11** framework with custom backbone modifications:

| Component | Implementation |
|-------------|----------------|
| Detection Framework | Ultralytics YOLO11 |
| Backbone | ResNet101 (via Timm library) |
| Integration | Custom YAML configs replacing default YOLO backbones |

**Key Modifications:**
- Replaced standard YOLO backbone with ResNet101 for enhanced feature extraction
- Optimized for crater-like morphology and varying lunar terrain textures
- Configured anchor boxes suitable for circular/elliptical crater shapes

---

## 📊 Results

### YOLO11 Model Performance

| Dataset | Precision | Recall | 
|---------|-----------|--------|
| **OHRC** | 0.756 | 0.708 | 
| **TMC-2** | 0.809 | 0.719 | 

**Training Details:**
- OHRC: Trained for 300 epochs
- TMC-2: Trained for 150 epochs

**Observations:**
- **OHRC:** Strong recall (66.8%) indicating good detection of actual craters, with balanced precision
- **TMC-2:** Higher precision (80.9%) but lower recall, suggesting conservative detection with fewer false positives
- Both models demonstrate effective localization under strict IoU thresholds (mAP@50-95)

**Output Artifacts:**
- Training graphs and visualizations: `results/graphs/`
- Model predictions: `results/predictions/`

**Trained Model:**
- The pre-trained YOLO11 model derived from this project can be downloaded from: https://drive.google.com/file/d/14ftYh3RbXBkaRviB-tl1X1O8uFLa90vI/view?usp=sharing

---

## 📁 Repository Structure

```
Lunar-Crater-Detection-01/
├── code/
│   └── yolo11/                    # YOLO11 implementation notebooks for OHRC & TMC-2
├── resourses/
│   ├── folderohr/                 # OHRC dataset tiles and annotations
│   └── foldertmc/                 # TMC-2 dataset tiles and annotations
├── results/
│   ├── graphs/                    # Training metrics and performance plots
│   └── predictions/               # Model inference outputs
├── yolo-custom-backbone-scripts/
│   └── yolo11/                    # Custom backbone YAML configs for YOLO11
├── LICENSE                        # MIT License
└── README.md                      # Project documentation
```

---

## 🚀 How to Use

1. Clone the repository:
    ```bash
    git clone https://github.com/your-username/lunar-crater-detector.git
    cd lunar-crater-detector
    ```

2. Navigate to the model directory:
    ```bash
    cd code/yolo11/
    ```

3. Open the Jupyter notebook for your dataset (OHRC or TMC-2)

4. Run through the cells to:
    - Load and visualize datasets from `resourses/folderohr/` or `resourses/foldertmc/`
    - Initialize and train the YOLO11 model
    - Evaluate and visualize detection outputs in `results/`

5. Customize model parameters or backbones via the `timm` interface in the notebook or modify configs in `yolo-custom-backbone-scripts/yolo11/`

---

## 🧩 Future Work

- Incorporation of **TMC-2 elevation data** to improve crater detection in shadowed/ambiguous regions.
- Enhanced labeling with tools like **ArcGIS Pro** for geospatial alignment.
- Experimentation with **segmentation-based models** for crater rims and interiors.
- Expansion to include datasets from other planetary bodies (e.g., Mars, Mercury).

---

## 📜 License

This project is released under the [MIT License](LICENSE).

---

## 🌌 Applications

- Automated planetary mapping  
- Surface age estimation  
- Lunar mission hazard planning  
- Geological feature extraction from high-res imagery

---

