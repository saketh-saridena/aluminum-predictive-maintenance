# Predictive Maintenance for Aluminum Manufacturing

A machine learning project developed for the **CU Boulder DaSSA Hackathon** that classifies bad decoating cycles in aluminum scrap processing. Achieved **94.38% accuracy** and **0.988 AUC-ROC** using Random Forest with SMOTE oversampling.

## Overview

Aluminum decoating removes coatings and organic contaminants from scrap via thermal pyrolysis. Poor cycles produce excess black dross, leading to significant costs:

- **Without detection:** $32,560 loss + $300/hr labor
- **With early detection:** $16,000 preventive maintenance (30 min)
- **Environmental:** Bad cycles produce 50kg extra black dross ($60/kg disposal)

The model classifies cycles as **Good (0)** or **Bad (1)** based on 18 operational sensor parameters, enabling timely maintenance scheduling.

## Key Results

| Metric | Value |
|--------|-------|
| **Accuracy** | **94.38%** |
| **AUC-ROC** | **0.988** |
| **Recall (Bad cycles)** | **94%** |
| Precision (Bad cycles) | 75% |
| F1-Score (Bad cycles) | 0.84 |

**Confusion Matrix:** 2,588 TN | 153 FP | 29 FN | 469 TP

## Dataset

- **16,504 training samples** with 18 sensor readings (B_2 to B_25)
- **4,127 test samples** for Kaggle submission
- Temporal data: March - May 2020 (5-minute intervals)
- Highly imbalanced: 13,719 good vs 2,474 bad cycles (5.5:1 ratio)

## Tech Stack

Python, scikit-learn (Random Forest, Logistic Regression), XGBoost, imbalanced-learn (SMOTE), pandas, matplotlib, seaborn

## Methodology

1. **Preprocessing:** Imputed missing values (mean for continuous, mode for categorical)
2. **Class Balancing:** Oversampling + SMOTE to handle 5.5:1 imbalance
3. **Model Selection:** Tested Logistic Regression, Random Forest, XGBoost
4. **Hyperparameter Tuning:** GridSearchCV with 3-fold CV (729 fits), optimized for Recall
5. **Final Model:** Random Forest with optimized hyperparameters

## Project Structure

```
├── Hackathon_final.ipynb           # Complete ML pipeline
├── Hackathon_final.html            # Rendered notebook
└── Predicted_Test_Data_Final.csv   # Kaggle submission predictions
```

## How to Run

1. Clone the repository
2. Install dependencies: `pip install xgboost scikit-learn imbalanced-learn pandas matplotlib seaborn`
3. Open and run `Hackathon_final.ipynb`
