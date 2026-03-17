# 🎭 Instance Segmentation with Mask R-CNN

> Pixel-level object detection and segmentation using Mask R-CNN on the MS-COCO dataset.

![Python](https://img.shields.io/badge/Python-3.7-blue?logo=python)
![TensorFlow](https://img.shields.io/badge/TensorFlow-1.x-orange?logo=tensorflow)
![Task](https://img.shields.io/badge/Task-Instance%20Segmentation-green)
![Dataset](https://img.shields.io/badge/Dataset-MS--COCO-lightgrey)

---

## 📌 Overview

This project demonstrates **instance segmentation** using [Mask R-CNN](https://arxiv.org/abs/1703.06870) (He et al., 2017) — a framework that simultaneously performs object detection, classification, and pixel-level mask prediction.

Unlike semantic segmentation (which labels every pixel with a class), instance segmentation distinguishes between **individual object instances** of the same class — e.g., detecting 3 separate people rather than one merged "person" region.

Key metric used: **Intersection over Union (IoU)** — measures overlap between predicted mask and ground truth.

---

## 🧠 Model Architecture

Mask R-CNN extends Faster R-CNN with a parallel **mask prediction branch**:

```
Input Image
    │
    ▼
ResNet + FPN Backbone  ──→  Feature Maps
    │
    ▼
Region Proposal Network (RPN)
    │
    ▼
RoIAlign (precise pixel alignment)
    │
    ├──→ Classification Head  (What class?)
    ├──→ Bounding Box Head    (Where is it?)
    └──→ Mask Head            (Which pixels?)
```

Pre-trained weights from MS-COCO (80 object categories) are used for inference.

---

## 🗂️ Repository Structure

```
mask-rcnn-segmentation/
├── Masked_RCNN_Image_Segmentation.ipynb   # Main notebook
├── images/                                 # Input test images
├── outputs/                                # Segmentation results
├── requirements.txt                        # Python dependencies
└── README.md
```

---

## ⚙️ Setup & Usage

### Prerequisites
- Python 3.7
- TensorFlow 1.x (use `%tensorflow_version 1.x` in Colab)
- Google Colab recommended (GPU runtime)

### Quick Start

**Option 1 — Google Colab (Recommended)**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

1. Upload `Masked_RCNN_Image_Segmentation.ipynb` to Colab
2. Set runtime to **GPU**
3. Run all cells — dependencies install automatically

**Option 2 — Local Setup**

```bash
git clone https://github.com/YOUR_USERNAME/mask-rcnn-segmentation.git
cd mask-rcnn-segmentation
pip install -r requirements.txt
jupyter notebook Masked_RCNN_Image_Segmentation.ipynb
```

### What the Notebook Does

| Step | Description |
|------|-------------|
| 1 | Install `h5py==2.10.0` and clone Matterport's Mask R-CNN repo |
| 2 | Clone COCO API and compile PythonAPI |
| 3 | Download pre-trained COCO weights (`mask_rcnn_coco.h5`) |
| 4 | Configure model for single-image inference |
| 5 | Run detection on a test image and visualise masks, bounding boxes, and confidence scores |

---

## 📦 Dependencies

```
tensorflow==1.x
h5py==2.10.0
numpy
scikit-image
matplotlib
pycocotools
```

> **Note:** This project uses TensorFlow 1.x due to compatibility with the Matterport Mask R-CNN implementation. For TF2 compatibility, see [this fork](https://github.com/akTwelve/Mask_RCNN).

---

## 📊 Sample Output

The model outputs per-image:
- **Bounding boxes** around each detected instance
- **Class labels** with confidence scores
- **Binary masks** at pixel level, colour-coded per instance

80 COCO classes supported, including: `person`, `car`, `dog`, `bicycle`, `chair`, and more.

---

## 📚 References

- He, K. et al. (2017). [Mask R-CNN](https://arxiv.org/abs/1703.06870). *ICCV 2017*.
- Matterport Mask R-CNN Implementation: [github.com/matterport/Mask_RCNN](https://github.com/matterport/Mask_RCNN)
- MS-COCO Dataset: [cocodataset.org](https://cocodataset.org/)

---

## 👩‍💻 Author

**Madhumitha Murthy**  
MSc Computer Control & Automation, Nanyang Technological University  
[LinkedIn](http://www.linkedin.com/in/madhumitha-murthy-4801b7223) · [GitHub](https://github.com/YOUR_USERNAME)
