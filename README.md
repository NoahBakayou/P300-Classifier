# P300: Detecting the P300 Component Using Machine Learning
#### Course Info: 
- CS 577 
- Dr. A
- Fall 2025

#### Authors: 
- Noah Bakayou 
- Pavithra Magendiran
- Noam Joseph
## Overview  
This project focuses on detecting the **P300 Event-Related Potential (ERP)** from EEG data collected during a 6×6 matrix-speller task. The P300 is a positive voltage peak that appears ~300 ms after a meaningful stimulus—specifically, the row and column containing the user’s intended character. Our goal is to classify **target flashes** vs. **non-target flashes** and build a machine learning system that can infer the user’s chosen character.

## Dataset  
We use **BCI Competition III – Dataset II Subject_A_Train.mat**. The subject data contains:

- **85 training epochs** and **100 test epochs**
- **64 EEG channels**, sampled at **240 Hz**
- **180 flashes per epoch** (15 sequences × 12 stimuli)  
  — See the official dataset documentation for further details.

**Key variables:**  
- `Signal` — EEG (epochs × samples × channels)  
- `Flashing` — marks when a row/column is flashed  
- `StimulusCode` — identifies which row/column (1–12)  
- `StimulusType` — target (1) or non-target (0)  
- `TargetChar` — correct character label (train only)

## Project Files
- **`src`** folder contains
  - **`P300.ipynb`**:Main notebook for flash-level and code-level feature extraction, exploratory data analysis, and initial logistic regression modeling.
  - **`HW5_SQL_and_Classification.ipynb`**: HW5 notebook using DuckDB SQL for data management and implementing Random Forest classification on code-averaged features for direct comparison with logistic regression.
- **`data`**: Main folder where our dataset is
- **`Reports`**: Main folder for 
  - Progress Report
  - Power Point Presentation
  - Final Report
- **`requirements.txt`** — Lists all Python dependencies needed to run the notebooks.

## Setup & Usage

1. **Clone the repository** or download the files to your local machine.
2. **Install dependencies:**  
   ```bash
   pip install -r requirements.txt
   source venv/bin/activate   # On Windows: venv\Scripts\activate
3. pip install -r requirements.txt
4. Launch Jupyter Notebook or VS Code, then open and run:
    - P300.ipynb for the original feature extraction and logistic regression analysis.
    - HW5_SQL_and_Classification.ipynb for SQL-based EDA and Random Forest modeling.

## Methods and Notebook Overview

- Flash-level and code-level feature extraction: Windowing (typically 0–600 ms), channel selection, and code-averaging.
- EDA: Both Python and DuckDB SQL queries to summarize class balance, feature distributions, and label statistics.
- Modeling: Standardization, PCA (sweep), and classification using logistic regression and random forest with careful train/validation/test splits to prevent data leakage.
- Results: Model comparison using confusion matrices, ROC curves, AUC and discussion of class imbalance challenges.