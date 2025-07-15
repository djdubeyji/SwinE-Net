# SwinE-Net: Hybrid Deep Learning for Polyp Segmentation

This repository contains our implementation of **SwinE-Net**, a hybrid deep learning framework for polyp segmentation and detection, inspired by the paper:  
“SwinE-Net: Hybrid deep-learning approach to novel polyp segmentation using convolutional neural network and Swin Transformer”  
by Kyeong-Beom Park and Jae Yeol Lee.

---

## Table of Contents

- [Overview](#overview)
- [Project Team](#project-team)
- [Directory Structure](#directory-structure)
- [Installation & Requirements](#installation--requirements)
- [How to Run](#how-to-run)
- [Data Preparation](#data-preparation)
- [Results](#results)
- [Project Phases](#project-phases)
- [References](#references)

---

## Overview

SwinE-Net is a hybrid segmentation model that combines the strengths of transformer-based (Swin Transformer) and convolutional (EfficientNet) backbones. The network is designed for accurate polyp segmentation in medical images, leveraging feature fusion, multi-scale dilated convolution (MDCB), and multi-scale feature aggregation (MFAB).

---

## Project Team

| Name              | Email                              |
|-------------------|------------------------------------|
| Pranjal Sharma    | pranjaldub [at] gmail [dot] com    |
| Hanisha Kasaraneni| kasaranenih [at] gmail [dot] com   |

Supervisor: **Prof. Karl Rohr**

---

## Directory Structure

```
├── polyp_segmentation.ipynb # Main model and training notebook
├── predicted_masks.zip      # Main model and training notebook
├── results/                 # Output results and visualizations
├── README.md                # This file
```

---

## Installation & Requirements

- **Python 3.8+**
- **PyTorch** (>=1.10)
- **timm** (for model backbones)
- **albumentations**, **Pillow**, **numpy**, **scikit-learn**, **torchmetrics**

---

## How to Run (Google Colab)

You can easily run and experiment with this project on [Google Colab](https://colab.research.google.com/), which provides free GPU resources and a convenient Jupyter notebook interface.

**Steps:**

1. **Open the Google Colab Notebook:**
    - You can upload your own notebook or use our template by clicking [here](https://colab.research.google.com/) and uploading the provided notebook, or by cloning this repository and opening a notebook in Colab.
    - Alternatively, click the "Open in Colab" badge if available.

2. **Clone the Repository:**
    ```python
    !git clone https://github.com/djdubeyji/SwinE-Net.git
    %cd SwinE-Net
    ```

3. **Prepare Data:**
    - Upload your images and masks to the Colab environment, ideally into a `data/` folder.
    - You can use `files.upload()` or mount Google Drive for larger datasets:
      ```python
      from google.colab import drive
      drive.mount('/content/drive')
      # Then copy/move your data as needed
      ```
    - Also, the code facilitates the download of the dataset automatically, only kaggle api key is required,

5. **Train the Model:**
    - Run the collab cells one by one.

7. **Download Results:**
    - After training, you can download predicted masks, results, or model using Colab's file browser or:
      ```python
      from google.colab import files
      files.download('path/to/your/file')
      ```

**Tip:** You can edit, visualize, and experiment interactively in Colab by converting the Python script to a notebook or by creating your own analysis cells.

---

## Data Preparation

- The dataset should have the following structure:
    ```
    data/
      images/
        img1.jpg
        img2.jpg
        ...
      masks/
        img1.jpg
        img2.jpg
        ...
    ```
- Masks should be binary (polyp area = white/1, background = black/0).
- By default, images and masks are resized to 224x224 during preprocessing.

---

## Results

| Metric       | Kvasir-SEG | ClinicDB |
|--------------|------------|----------|
| Mean IoU     |   0.928    |  0.907   |
| Mean Dice    |   0.866    |  0.830   |
| Accuracy     |   0.976    |  0.982   |


---

## Project Phases

### Phase 1: Literature Review and Dataset Exploration
In this initial phase, we conducted an extensive literature review of recent advancements in medical image segmentation, focusing on transformer-based and hybrid deep learning models. We carefully studied the SwinE-Net paper to understand its motivations, architectural choices, and evaluation strategies. Simultaneously, we explored the available polyp segmentation datasets, such as Kvasir-SEG and ClinicDB, to assess data quality, annotation consistency, and suitability for our experiments. This phase laid the groundwork for our implementation, ensuring we had both a solid theoretical foundation and clearly defined data requirements.

### Phase 2: Model Implementation and Architecture Design
We implemented the SwinE-Net architecture using PyTorch, faithfully replicating the hybrid encoder structure with Swin Transformer and EfficientNet backbones. Special attention was given to the design of feature fusion, MDCB (Multi-scale Dilated Convolution Block), and MFAB (Multi-scale Feature Aggregation Block) modules, as these are critical for capturing both local and global context in segmentation tasks. We also incorporated robust data augmentation pipelines using Albumentations to improve model generalization. This phase involved iterative coding, debugging, and initial ablation studies to confirm the integrity of our model components.

### Phase 3: Training, Hyperparameter Tuning, and Evaluation
During this phase, we trained our model on the prepared datasets, experimenting with various training strategies, optimizers, and learning rate schedules. We rigorously tuned hyperparameters such as learning rate, batch size, and augmentation strength to maximize segmentation performance. Evaluation metrics including Dice coefficient, IoU, and pixel accuracy were tracked on both validation and test splits. We also performed cross-dataset validation to assess the model's robustness and generalization abilities, comparing our results against existing baselines and the original SwinE-Net paper.

### Phase 4: Analysis, Ablation Study, and Report Preparation
In the final phase, we analyzed our experimental results in depth, identifying strengths and areas for improvement in our approach. We conducted ablation studies to isolate the contributions of different architectural components (e.g., MDCB, MFAB, and feature fusion strategies). Visualizations of segmentation outputs were generated to qualitatively assess model predictions. Finally, we compiled our findings into a comprehensive report, detailing our methodology, results, insights, and potential directions for future work.

---

## References

- Park, K.-B., & Lee, J. Y. (2023). SwinE-Net: Hybrid deep-learning approach to novel polyp segmentation using convolutional neural network and Swin Transformer.
- [Swin Transformer (official repo)](https://github.com/microsoft/Swin-Transformer)
- [EfficientNet (official repo)](https://github.com/lukemelas/EfficientNet-PyTorch)

---

## Acknowledgements

Special thanks to Prof. Karl Rohr for supervision and guidance.

---

**For questions or issues, please open an issue on this repository.**
