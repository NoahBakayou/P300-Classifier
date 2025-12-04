# P300 EEG Classification — CS 577 Project  
### Detecting the P300 Component Using Machine Learning

## Overview  
This project focuses on detecting the **P300 Event-Related Potential (ERP)** from EEG data collected during a 6×6 matrix-speller task. The P300 is a positive voltage peak that appears ~300 ms after a meaningful stimulus—specifically, the row and column containing the user’s intended character. Our goal is to classify **target flashes** vs. **non-target flashes** and build a machine learning system that can infer the user’s chosen character.

## Dataset  
We use **BCI Competition III – Dataset II**, which includes EEG from two subjects. Each subject’s data contains:

- **85 training epochs** and **100 test epochs**  
- **64 EEG channels**, sampled at **240 Hz**  
- **180 flashes per epoch** (15 sequences × 12 stimuli)  
  — documented in the official dataset description :contentReference[oaicite:0]{index=0}

Key variables:  
- `Signal` — EEG (epochs × samples × channels)  
- `Flashing` — marks when a row/column is flashed  
- `StimulusCode` — identifies which row/column (1–12)  
- `StimulusType` — target (1) or non-target (0)  
- `TargetChar` — correct character label (train only)

## Methods Completed  
- Loaded and validated all `.mat` files using `scipy.io.loadmat` 
- Extracted flash-aligned EEG windows (0–700 ms)  
- Built target vs. non-target datasets:  
  - ~2,537 target segments  
  - ~12,678 non-target segments  
- Confirmed clear P300 positivity around ~300 ms through averaged ERP plots  
- Implemented a baseline classifier:  
  - Standardization → PCA → Logistic Regression (`class_weight="balanced"`)  
  - Achieved ROC-AUC ≈ **0.62** on flash-level prediction

## Next Steps  
- Implement **code-level averaging** (combine 15 flashes per row/column)  
- Compare flash-level vs. averaged code-level accuracy  
- Test different EEG channel sets (Cz, FC1, CPz, etc.)  
- Refine PCA components and evaluate model performance

## Team  
Noah Bakayou, Pavithra Magendiran, Noam Joseph  
