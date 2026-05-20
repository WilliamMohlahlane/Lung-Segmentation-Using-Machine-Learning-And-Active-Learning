# Lung-Segmentation-Using-Machine-Learning-And-Active-Learning

**Author:** W. Mohlahlane  
**Institution:** University of the Western Cape, Bellville, South Africa  
**Programme:** Honours 2026



## Overview

This research investigates whether active learning can reduce the amount of data that must be labelled for lung segmentation. It is based on the challenge that machine learning models require large amounts of annotated CT image data, while manual annotation is slow, expensive, and often requires expert input. To address this, the study will apply active learning to a U-Net machine learning model that performs lung segmentation, with the aim of selecting only the most informative samples for annotation and determining whether results close to full dataset annotation can still be achieved.

## Repository Structure

```text
.
├── Model.ipynb  
|
├── best_lung_segmentation_model.keras
│   
├── .gitignore
|
├── README.md
|
|── lung_mask/
|    ├── conronacases_001.nii
│    └── conronacases_002.nii
|    |── ...
|    └── radiopaedia_4086625_0.nii
|
├── ct_scans/
|    ├── conronacases__org_001.nii
│    └── conronacases__org_002.nii
|    |── ...
|    └── radiopaedia_org_covid-19-pneumonia-40_86625_0-dcm.nii


```

## Dataset

**COVID-19 CT Lung and Infection Segmentation Dataset**  
- Published by Ma Jun et al. (2020), available on [Kaggle](https://www.kaggle.com/) and [Zenodo](https://zenodo.org/record/3757476).
- 20 chest CT scans from COVID-19 patients, sourced from the Coronacases Initiative and Radiopaedia.
- Each scan has a corresponding lung mask annotated by two radiologists and verified by an experienced radiologist.
- Scans are stored in NIfTI format (`.nii`) and loaded using the NiBabel library.

After extracting 2D axial slices from all 3D volumes, the dataset contains 3,520 slices in total.

## U-Net Architecture

The model is based on the U-Net encoder-decoder architecture commonly used in biomedical image segmentation.

### Components

- Encoder (downsampling path)
- Bottleneck layer
- Decoder (upsampling path)
- Skip connections

The final layer uses a sigmoid activation function for binary segmentation.

## Requirements

### Software

| Library | Purpose |
|---|---|
| Python 3.x | Runtime |
| TensorFlow / Keras | Model building, training, and evaluation |
| NumPy | Array operations and data handling |
| NiBabel | Loading `.nii` CT scan volumes |
| scikit-image | Image resizing and preprocessing |
| scikit-learn | Train/validation/test splitting |
| Matplotlib | Visualisation of results |



Install dependencies with:

```bash
pip install tensorflow numpy nibabel scikit-image scikit-learn matplotlib
```
## Setup

1. **Clone the repository** or download the project files.

2. **Download the dataset** from [Zenodo](https://zenodo.org/record/3757476) or Kaggle and place files in the correct folders:
   - CT scan volumes → `ct_scans/`
   - Lung mask volumes → `lung_mask/`

3. **Update the data paths** in `Model.ipynb` to point to your local directories:

```python
IMAGE_DIR = r"path/to/ct_scans"
MASK_DIR  = r"path/to/lung_mask"
```

4. **Open and run `Model.ipynb`** in Jupyter Notebook or VS Code.

---