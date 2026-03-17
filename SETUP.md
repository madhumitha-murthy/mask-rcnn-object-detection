# Setup Guide

## Running on Google Colab (Recommended)

Google Colab is recommended because:
- Free GPU access
- TensorFlow 1.x available via magic command
- No local environment setup needed

### Steps

1. Go to [colab.research.google.com](https://colab.research.google.com)
2. Upload `Masked_RCNN_Image_Segmentation.ipynb`
3. Go to **Runtime → Change runtime type → GPU**
4. Run the first cell: `%tensorflow_version 1.x` — this must be run **before** any TF import
5. Run all remaining cells in order

### Common Issues

**h5py version conflict**  
The notebook pins `h5py==2.10.0`. This is intentional — newer versions break Keras model loading in TF1. The `--force-reinstall` flag handles this.

**`metrics_tensors` AttributeError**  
Cell 11 patches this automatically by injecting `self.keras_model.metrics_tensors = []` into `mrcnn/model.py`.

**COCO API build fails on Windows**  
Use Colab or Linux. The `make` command in the COCO API setup requires a Unix environment.

---

## Running Locally (Advanced)

Requires Linux or macOS with Python 3.7.

```bash
# Create a virtual environment
python3.7 -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Install COCO API
git clone https://github.com/cocodataset/cocoapi.git
cd cocoapi/PythonAPI && make && cd ../..

# Clone Mask RCNN
git clone https://github.com/matterport/Mask_RCNN
cd Mask_RCNN && pip install -r requirements.txt && python setup.py install && cd ..

# Download weights
wget https://github.com/matterport/Mask_RCNN/releases/download/v2.0/mask_rcnn_coco.h5

# Launch notebook
jupyter notebook Masked_RCNN_Image_Segmentation.ipynb
```
