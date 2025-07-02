# Breast Cancer Prediction using Neural Network and Feature Sensitivity Analysis

# Project Overview

This project aims to predict whether a tumor is **malignant** or **benign** using the **Wisconsin Breast Cancer Dataset**. A neural network model was trained for classification, and explainability techniques were used to understand the decision-making process of the model.

---

# Objectives

- Train a neural network to classify breast cancer (malignant vs benign).
- Analyze data for quality and feature relevance.
- Perform **feature importance** analysis using:
  - Random Forest (global importance)
  - σ-variation Sensitivity Plots (local instance-level importance)
- Observe how **feature influence varies** between instances.

---

# Dataset Details

- **Source**: `sklearn.datasets.load_breast_cancer()`
- **Samples**: 569
- **Features**: 30 numeric features + 1 target column
- **Target**:  
  - `0` = Malignant  
  - `1` = Benign

---

# Preprocessing

- No null values
- No duplicate entries
- Normalized features using Min-Max scaling
- Performed **feature correlation analysis**
- Checked **class imbalance** (Benign: ~62%, Malignant: ~37%)

---

# Model Summary

- **Model**: Feedforward Neural Network (Keras)
- **Accuracy**: 100% on test set (for evaluated instances)
- **Train/Test Split**: 80/20
- **Loss Function**: Binary Crossentropy
- **Optimizer**: Adam

---

# Explainability Techniques Used

### 1. **Random Forest Feature Importance (Global)**

Ranked top features overall:
- `worst perimeter`
- `worst radius`
- `worst concave points`
- `worst area`

### 2. **σ-variation Sensitivity Analysis (Local)**

- For a chosen test instance, each feature was varied ±3σ.
- Observed model's prediction sensitivity to these perturbations.
- Found that some features (like `worst concave points`) had high impact on some instances, but not on others.

---

# Key Takeaways

- **Global feature importance** is useful for identifying overall trends.
- **Local sensitivity analysis** helps explain **individual predictions** — critical in healthcare.
- Feature impact varies **from patient to patient**, so explainability must be personalized.

---

# Final Conclusion

While features such as `worst perimeter` and `worst concave points` were globally important, local sensitivity analysis showed that the **impact of features depends on the specific input instance**. This highlights the importance of **combining global and local explainability** for better understanding and trust in AI models, especially in sensitive domains like medicine.


---

# References

- [Scikit-learn Breast Cancer Dataset](https://scikit-learn.org/stable/datasets/toy_dataset.html#breast-cancer-dataset)
- [Keras](https://keras.io/)
- [Sensitivity Analysis Concepts](https://en.wikipedia.org/wiki/Sensitivity_analysis)
