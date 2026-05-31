# Philippine Household Income Analysis
### End-to-End Machine Learning Pipeline
### Filipino Family Income and Expenditure Survey (FIES) — PSA, 2021
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1_4VB0mZc1DtJjPdp2jwPs1dHfjEZSPx-)
---

## The Question

Can we predict whether a Philippine household earns 
above or below the median monthly income — using only 
observable characteristics like spending habits, 
household profile, and asset ownership?

If yes, the implications go beyond prediction accuracy: 
social programs and policymakers could identify 
households that need support even without direct 
income data.

---

## The Dataset

**Source:** Philippine Statistics Authority (PSA)  
**Survey:** Family Income and Expenditure Survey (FIES), 2021  
**Size:** 41,544 household records · 64 variables  
**Coverage:** Income, expenditure, assets, household 
demographics, and regional data across the Philippines

**Classification target:** Binary — above or below 
the median monthly income of ₱13,673

---

## Pipeline Overview

```
1. Load & Explore          EDA across 64 variables
2. Visualize Key Patterns  Income distribution, regional 
                           gaps, expenditure breakdown
3. Engineer Target         Binary income class 
                           (above/below ₱13,673 median)
4. Clean & Preprocess      Encoding, scaling, 
                           train/test split
5. Train Classifiers       5 models — leaderboard output
6. Train Regressors        5 models — leaderboard output
7. Evaluate & Compare      Accuracy, F1, R², MAE, MAPE, 
                           RMSE across all 10 models
```

---

## Key EDA Findings

- **Income is right-skewed:** the mean monthly income 
  sits significantly above the median (₱13,673) — 
  a small number of high-income households pull the 
  average up
- **Regional gap is stark:** NCR and CALABARZON 
  consistently lead in median income; Mindanao and 
  BARMM regions sit at the lower end — consistent 
  with known development disparities
- **Food dominates expenditure:** the single largest 
  spending category across all income classes — a 
  hallmark of lower-to-middle income economies
- **Income source shapes risk:** wage/salary earners 
  have tighter, more predictable income ranges; 
  entrepreneurial households show much wider spread

---

## Models Trained

### Classifiers — Predicting Income Class (Above / Below Median)

| Model | Type |
|---|---|
| Logistic Regression | Linear baseline |
| Random Forest | Ensemble — bagging |
| Gradient Boosting | Ensemble — boosting |
| Decision Tree | Single tree baseline |
| K-Nearest Neighbors | Instance-based |

**Metrics:** Accuracy · Precision · Recall · F1 Score

### Regressors — Predicting Exact Monthly Income (₱)

| Model | Type |
|---|---|
| Linear Regression | Linear baseline |
| Ridge Regression | Regularized linear |
| Random Forest Regressor | Ensemble — bagging |
| Gradient Boosting Regressor | Ensemble — boosting |
| Decision Tree Regressor | Single tree baseline |

**Metrics:** MAE · MAPE · RMSE · R²

---

## Tech Stack

```
Python · pandas · NumPy · scikit-learn
matplotlib · seaborn · Google Colab
```

---

## File Structure

```
philippine-fies-income-analysis/
├── fies_income_analysis.ipynb  ← Full pipeline notebook
├── requirements.txt
├── .gitignore
└── LICENSE
```

---

## Context

Solo project completed as part of  
**Uplift Code Camp — Python for Data and AI Bootcamp, 2026**

Dataset source: [Philippine Statistics Authority — FIES 2021](https://psa.gov.ph)
