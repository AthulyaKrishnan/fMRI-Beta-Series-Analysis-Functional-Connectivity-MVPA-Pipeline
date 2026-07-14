[Final_IEL_readme.docx](https://github.com/user-attachments/files/28539208/Final_IEL_readme.docx)

# fMRI Beta-Series Analysis, Functional Connectivity & Machine Learning Pipeline

This repository contains analysis pipelines developed for an ongoing task-based fMRI study conducted at the Indian Institute of Science (IISc), Bengaluru. The project combines traditional neuroimaging methods with machine learning to investigate how emotional and reward-related conditions are represented in brain activity.

The repository focuses on the analysis workflow rather than the dataset itself. As the study is currently unpublished, participant data and group-level results are not included. The code is provided to demonstrate the implementation of the preprocessing, feature extraction, functional connectivity, and machine learning pipelines.

---

## Features

The repository includes workflows for:

- Trial-wise event extraction from behavioural log files
- Single-trial beta estimation using AFNI Least Squares Sum (LSS)
- ROI-based voxel-wise beta extraction
- Functional connectivity analysis
- Multivariate Pattern Analysis (MVPA)
- Machine learning classification using classical models and neural networks
- Cross-validation and model evaluation

---

## Analysis Pipeline

### 1. Behavioural Data Processing

Behavioural event files are extracted from MATLAB log files and converted into participant-level datasets.

The pipeline includes:

- Run-wise event extraction
- Condition labelling
- Behavioural measures (reaction time and accuracy)
- Trial filtering
- Outlier removal
- Metadata generation

Output:

- Trial-wise behavioural dataset used throughout the analysis pipeline.

---

### 2. Single-Trial Beta Estimation

Whole-brain single-trial beta maps are estimated using AFNI's Least Squares Sum (LSS) framework.

The shell scripts perform:

- GLM estimation
- Motion regression
- Censoring
- Trial-specific beta estimation
- Export of trial-wise beta images

Output:

- One beta image for every trial.

---

### 3. ROI Beta Extraction

Voxel-wise beta values are extracted from predefined Regions of Interest (ROIs) using Nilearn masking.

The pipeline performs:

- ROI masking
- Resampling to functional space
- Voxel-wise beta extraction
- Quality-control checks
- Metadata generation

Output:

- Trial-wise voxel feature matrices for each ROI.

---

### 4. Functional Connectivity Analysis

Functional connectivity is estimated using trial-wise beta-series correlations.

The pipeline computes:

- ROI-to-ROI correlation matrices
- Seed-to-voxel connectivity maps
- Fisher Z-transformed connectivity maps

These connectivity features are subsequently used for machine learning classification.

---

### 5. Machine Learning

The repository contains two decoding approaches.

#### ROI Beta-Series Decoding

Voxel-wise beta estimates are used as input features for binary classification.

Implemented models include:

- Logistic Regression
- Linear Support Vector Classifier (Linear SVC)
- Feed-forward Neural Network

Evaluation is performed using Leave-One-Trial-Out (LOTO) cross-validation.

Performance metrics include:

- Accuracy
- Confusion Matrix

---

#### Functional Connectivity Classification

ROI-to-ROI functional connectivity coefficients are extracted from correlation matrices and used as features for multi-class classification.

A simple feed-forward neural network is trained to classify four experimental conditions using Leave-One-Subject-Out cross-validation.

---

## Repository Structure

```text
├── Behavioural Processing
├── AFNI LSS Beta Estimation
├── ROI Beta Extraction
├── Functional Connectivity
├── MVPA
└── Machine Learning
```

---

## Python Packages

- AFNI
- Python
- NumPy
- Pandas
- SciPy
- Nilearn
- Scikit-learn
- TensorFlow / Keras
- Matplotlib
- Seaborn

---

## Methods

This repository demonstrates several widely used neuroimaging and machine learning techniques, including:

- Least Squares Sum (LSS) single-trial modelling
- ROI-based feature extraction
- Beta-series functional connectivity
- Multivariate Pattern Analysis (MVPA)
- Logistic Regression
- Linear Support Vector Machines
- Feed-forward Neural Networks
- Leave-One-Subject-Out Cross-Validation
- Permutation-based statistical inference

---

## Notes

This repository is intended to document the analytical framework used in the study. Participant data and group-level results are not publicly available because the work is currently under review. The code has been shared to improve transparency, reproducibility, and to demonstrate the implementation of the analysis pipelines.

---

## Future Work

Potential extensions include:

- Representational Similarity Analysis (RSA)
- Deep learning for voxel-wise decoding
- Graph neural networks for functional connectivity
- Group-level mixed-effects modelling
