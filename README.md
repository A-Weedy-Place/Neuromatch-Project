
# Decoding Reward Sensitivity from fMRI using HCP Data

This project investigates whether resting-state fMRI (rs-fMRI) can predict individual differences in brain responses during reward processing, as observed in a gambling task using task-based fMRI (tfMRI). We used data from the Human Connectome Project (HCP) and applied machine learning techniques on Glasser-parcellated brain regions.

---

## 📊 Objectives

1. **Decode win vs. loss trials** from tfMRI using SVM models.
2. **Identify most predictive brain regions (ROIs)** using SVM weights.
3. **Use rs-fMRI data to predict**:
   - Accuracy of tfMRI-based models (reward sensitivity proxy).
   - BOLD contrast in key ROIs (win-loss differences).
   - Functional connectivity correlations with model performance.

---

## 🧠 Dataset

- **Source**: [Human Connectome Project (HCP)](https://www.humanconnectome.org/)
- **Subjects**: 338 individuals
- **Parcellation**: Glasser 360 cortical ROIs
- **Modalities**: Resting-state fMRI, Gambling task-based fMRI
- **Time resolution (TR)**: 0.72 seconds

---

## 🛠️ Methodology

### 1️⃣ Task-fMRI Decoding (Part 1)
- Extracted trial-level average BOLD signals for 5 TRs post-onset from gambling task.
- Labels: `0 = loss`, `1 = win`.
- Trained **subject-specific SVM classifiers** to predict win/loss from 360 ROI features.
- Collected:
  - Accuracy per subject
  - ROI weights from trained SVMs
- Averaged weights across subjects to identify **top 10 predictive ROIs**.

### 2️⃣ Resting-State fMRI Predictive Analysis (Part 2)
- Computed average BOLD signals for each ROI from rs-fMRI.
- Correlated rs-fMRI features with:
  - SVM accuracy (Pearson r ≈ 0.3 max)
  - Win-loss contrast in tfMRI ROIs using Lasso Regression (R² < 0.05)

### 🔬 Functional Connectivity (as mentioned in presentation)
- Correlated ROI-to-ROI FC features with SVM accuracy.
- Top 10 positively and negatively correlated FC pairs reported (not in code, mentioned in slides).

---

## 🧪 Models Used

- **Support Vector Machine (SVM)** – best accuracy, used for ROI selection.
- **Lasso Regression** – tested for predicting contrast using rs-fMRI.
- **Random Forest**
- **XGBoost**

---

## 📉 Results

| Analysis | Key Outcome |
|----------|-------------|
| SVM decoding (tfMRI) | Successful, individual variability observed |
| Top ROIs | Orbitofrontal cortex, ACC, Inferior frontal gyrus |
| rs-fMRI average BOLD → SVM accuracy | Weak correlation (r < 0.3) |
| rs-fMRI average BOLD → ROI contrast | R² < 0.05 (non-significant) |
| rs-fMRI FC → SVM accuracy | Weak-to-moderate correlations observed |

---

## 🔍 Limitations

- Subcortical regions (e.g., striatum, amygdala) were **not included**.
- rs-fMRI poorly predicts individual differences in task performance.
- ROI selection limited to cortical Glasser parcellations.

---

## 📌 Future Directions

- Include subcortical ROIs in analysis.
- Explore deep learning models or graph-based methods.
- Investigate reward processing dynamics over time.

---

## 🙏 Acknowledgements

We thank **Jacob Morra** for guidance and support, and **Neuromatch Academy** for providing curated HCP data.

---

## 📎 References

- Barch et al. (2013), Neuroimage
- Glasser et al. (2016), Nature
- Cohen et al. (2020), Human Brain Mapping
- Delgado et al. (2000), J Neurophysiology
- Rolls et al. (2000), Cerebral Cortex
- Rogers et al. (2004), Biological Psychiatry
