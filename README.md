# Alzheimer’s Disease Prediction (Machine Learning Project)

## Overview

This project develops machine learning models to predict Alzheimer’s disease using demographic, lifestyle, and clinical data.

The primary goal is to evaluate how feature selection, model choice, and regularization impact predictive performance, while comparing linear and non-linear approaches.

---

## Objectives

- Predict Alzheimer’s diagnosis (0 = No, 1 = Yes)  
- Compare a baseline model (lifestyle features only) vs. a full-feature model  
- Evaluate performance using:
  - Accuracy  
  - Precision / Recall  
  - ROC-AUC  
- Analyze the impact of regularization and dimensionality reduction  

---

## Dataset

- **Source:** Kaggle Alzheimer’s Disease Dataset  
- **Author:** Rabie El Kharoua (2024)  
- **Link:** https://www.kaggle.com/dsv/8668279  

**Feature Categories:**
- Demographic (age, gender)  
- Lifestyle (smoking, BMI, etc.)  
- Clinical and cognitive indicators  

This dataset is for educational purposes only and is not intended for clinical use.

---

## Models Used

### Logistic Regression
- Feature scaling using `StandardScaler`  
- Regularization tuning (C values)  
- Interpretable coefficients  

### Random Forest
- Ensemble model capturing non-linear relationships  
- Tuned with `n_estimators = 200`  
- Used for performance comparison  

---

## Methodology

### Data Exploration
- Checked missing values, data types, and distributions  
- Identified class imbalance  
- Addressed using:
    - `class_weight = 'balanced'`  

---

### Baseline Model (Lifestyle Features Only)

- Logistic Regression and Random Forest trained on lifestyle features only  
- Demonstrated limited predictive performance  
- Established a baseline for comparison  

---

### Full Feature Model

- Included demographic, lifestyle, and clinical features  
- Resulted in significant improvement in all evaluation metrics  

---

### Regularization Tuning (Logistic Regression)

Tested:
- C = 1  
- C = 0.1  
- C = 0.01  

Best performance achieved with:

- **C = 0.01**
  - Reduced overfitting  
  - Improved generalization  

---

### PCA (Dimensionality Reduction)

To evaluate the effect of dimensionality reduction, PCA was applied to the full feature set.

Tested:
- Full feature model (no PCA)  
- PCA (95% variance retained)  
- PCA (10 components)  

**Results:**

| Model | Accuracy | Recall (Alzheimer’s) |
|------|--------|---------------------|
| Full Feature Model | ~0.81 | ~0.85 |
| PCA (95% Variance) | ~0.81 | ~0.80 |
| PCA (10 Components) | ~0.70 | ~0.63 |

**Conclusion:**

PCA did not improve model performance. While dimensionality was reduced, important predictive information was lost, leading to decreased recall and overall performance.

---

## Results

### Final Model: Tuned Random Forest

| Metric | Score |
|--------|------|
| Accuracy | ~0.93 |
| Recall (Alzheimer’s) | ~0.87 |
| ROC-AUC | ~0.93 |

---

## Model Performance

### Logistic Regression

#### Confusion Matrix
![Logistic Regression Confusion Matrix](images/confusion_matrix_lr.png)

The logistic regression model achieves high recall (~0.85), correctly identifying most Alzheimer’s cases. This reduces false negatives, which is critical in medical prediction tasks.

---

### Random Forest

#### Confusion Matrix
![Random Forest Confusion Matrix](images/confusion_matrix_rf.png)

The Random Forest model achieves stronger overall classification performance, improving both accuracy (~0.93 )recall (~0.87). This suggests that non-linear relationships in the data enhance predictive capability.

---

### ROC Curve
![ROC Curve](images/roc_curve_comparison.png)

The ROC curve demonstrates strong class separability, with both models achieving high AUC values (0.88 and 0.93 for Logistic Regression and Random Forest respectively).

---

## Model Comparison

- Random Forest outperformed logistic regression across all evaluation metrics:
  - Higher accuracy  
  - Higher recall (Alzheimer’s cases)  
  - Higher ROC-AUC  

- This indicates that **non-linear relationships significantly improve predictive performance**

- Logistic regression remains valuable due to:
  - Interpretability  
  - Clear feature importance via coefficients  

---

## Key Insights

- Lifestyle features alone are insufficient for accurate prediction  
- Clinical and cognitive features significantly improve performance  
- Regularization improves generalization in logistic regression  
- Random Forest captures complex, non-linear relationships effectively  

---

## Conclusion

The Random Forest model achieved the best overall performance across all evaluation metrics, including accuracy, recall, and AUC, making it the most effective model for this task.

These results suggest that non-linear relationships in the data play a significant role in predicting Alzheimer’s disease.

While logistic regression provides strong interpretability and a reliable baseline, Random Forest offers superior predictive performance and is better suited for this classification problem.

---

## Tech Stack

- Python  
- Pandas  
- Scikit-learn  
- Matplotlib  

---

## Project Structure
alzheimers-ml-prediction/
│
├── images/
│ ├── confusion_matrix_lr.png
│ ├── confusion_matrix_rf.png
│ ├── roc_curve.png
│
├── notebooks/
| |── Alzheimer's Disease Prediction Using Logistic Regression and Random Forest.ipynb
├── README.md

---

## Future Improvements

- Add cross-validation for more robust evaluation  
- Perform hyperparameter tuning (GridSearchCV / RandomizedSearchCV)  
- Explore advanced models (XGBoost, LightGBM)  
- Perform feature engineering and selection  
- Improve model interpretability (e.g., SHAP values)  

---

## Acknowledgements

This project uses the following dataset:

@misc{rabie_el_kharoua_2024,  
title={Alzheimer's Disease Dataset},  
url={https://www.kaggle.com/dsv/8668279},  
DOI={10.34740/KAGGLE/DSV/8668279},  
publisher={Kaggle},  
author={Rabie El Kharoua},  
year={2024}  
}

