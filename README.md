# 🌕 Lunar Crater Detection using Chandrayaan-2 Imagery

This repository presents an end-to-end pipeline for detecting lunar craters using high-resolution imagery captured by ISRO's **Chandrayaan-2** mission. The system leverages state-of-the-art deep learning object detection models, enhanced with custom backbone architectures from the [Timm](https://github.com/huggingface/pytorch-image-models) library.

---

## 📌 Project Overview

This project addresses the challenge of automated lunar crater detection—a critical task for planetary mapping, surface age estimation, and mission planning. Using imagery from Chandrayaan-2's Orbiter High Resolution Camera (OHRC) and Terrain Mapping Camera-2 (TMC-2), we developed and evaluated multiple YOLO-based detection models with custom ResNet101 backbones.

**Key Objectives:**
- Detect craters of varying sizes in high-resolution lunar imagery
- Compare performance across different YOLO architectures (YOLO11, YOLO12)
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

---

## 🧠 Model Architecture

The detection system is built on Ultralytics YOLO frameworks with custom backbone modifications:

| Component | Implementation |
|-------------|----------------|
| Detection Framework | Ultralytics YOLO11 / YOLO12 |
| Backbone | ResNet101 (via Timm library) |
| Integration | Custom YAML configs replacing default YOLO backbones |

**Key Modifications:**
- Replaced standard YOLO backbones with ResNet101 for enhanced feature extraction
- Optimized for crater-like morphology and varying lunar terrain textures
- Configured anchor boxes suitable for circular/elliptical crater shapes

---

## 📊 Results

### YOLO12 Model Performance

| Dataset | Precision | Recall | mAP@0.50 | mAP@0.50:0.95 |
|---------|-----------|--------|----------|---------------|
| **OHRC** | 0.746 | 0.668 | 66.7% | 32.4% |
| **TMC-2** | 0.809 | 0.519 | 58.7% | 33.7% |

**Observations:**
- **OHRC:** Strong recall (66.8%) indicating good detection of actual craters, with balanced precision
- **TMC-2:** Higher precision (80.9%) but lower recall, suggesting conservative detection with fewer false positives
- Both models demonstrate effective localization under strict IoU thresholds (mAP@50-95)

---

## 📁 Repository Structure

```
Lunar-Crater-Detection-01/
├── code/
│   ├── yolo11/          # YOLO11 implementation for OHRC & TMC-2
│   └── yolo12/          # YOLO12 implementation for OHRC & TMC-2
├── yolo-custom-backbone-scripts/
│   ├── yolo11/          # Custom backbone configs for YOLO11
│   └── yolo12/          # Custom backbone configs for YOLO12
└── README.md
```

**Notebooks:** The training and evaluation code is available as Jupyter notebooks within the `code/` directory for each model variant.

---

## 🚀 How to Use

1. Clone the repository:
    ```bash
    git clone https://github.com/your-username/lunar-crater-detector.git
    cd lunar-crater-detector
    ```

2. Navigate to the relevant model directory (`code/yolo11/` or `code/yolo12/`)

3. Open the Jupyter notebook for your dataset (OHRC or TMC-2)

4. Run through the cells to:
    - Load and visualize datasets
    - Initialize and train the YOLO model
    - Evaluate and visualize detection outputs

5. Customize model parameters or backbones via the `timm` interface in the notebook

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

