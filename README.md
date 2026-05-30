# Philippine Household Income Analysis
### End-to-End Machine Learning Pipeline — FIES 2021

An end-to-end machine learning pipeline built on the **2021 Family Income and Expenditure Survey (FIES)** dataset published by the Philippine Statistics Authority (PSA). The project runs two parallel tasks: classifying households by income bracket and predicting actual monthly income using regression.

---

## The Problem

The Philippines has significant income inequality, but direct income data is not always available for policy targeting. This project asks: **can we predict a household's income class from observable characteristics alone** — appliances owned, house type, education level, spending patterns — without relying on self-reported income figures?

If yes, social programs and policymakers can identify underserved households more efficiently using indirect signals that are easier to verify.

---

## Dataset

**Source:** [Philippine Statistics Authority — Family Income and Expenditure Survey (FIES)](https://psa.gov.ph/statistics/income-expenditure/fies)

| Detail | Value |
|---|---|
| Rows | 41,544 households |
| Columns | 64 features |
| Coverage | All regions of the Philippines |
| Median Monthly Income | ₱13,673.29 |

> **Note:** The dataset is not included in this repository. Download the FIES 2021 dataset from the PSA website and save it as `Family_Income_and_Expenditure_edited.csv` in the project root before running the notebook.

**Key feature categories:**
- Household expenditure (food, housing, transport, education, medical)
- Household head profile (age, sex, education, occupation, employment class)
- Asset ownership (appliances, vehicles, communication devices)
- Housing characteristics (type, materials, floor area, tenure status)
- Utilities access (water, electricity, toilet facilities)

---

## Pipeline Overview

```
1. Load & Explore          — EDA, shape, missing values, data types
2. Visualize Key Patterns  — Income distribution, regional breakdown, feature correlations
3. Engineer Target         — Binary income class (above/below median monthly income)
4. Clean & Preprocess      — Encoding, scaling, train/test split
5. Train ML Models         — 5 classifiers + 5 regressors run in parallel
6. Evaluate & Compare      — Leaderboard tables and comparison charts
7. Interpret Results       — Feature importance, confusion matrix, actual vs. predicted
```

---

## Results

### Task 1 — Classification
**Goal:** Predict whether a household earns above or below the median monthly income (₱13,673.29)

| Rank | Model | Accuracy |
|---|---|---|
| 1 | Random Forest Classifier | Best |
| 2 | Gradient Boosting Classifier | — |
| 3 | Logistic Regression | — |
| 4 | Decision Tree Classifier | — |
| 5 | K-Nearest Neighbors | — |

### Task 2 — Regression
**Goal:** Predict actual monthly income as a continuous value

| Rank | Model | R² | MAE | RMSE |
|---|---|---|---|---|
| 1 | Gradient Boosting Regressor | 0.8791 | ₱3,928.99 | ₱7,799.08 |
| 2 | Random Forest Regressor | — | — | — |
| 3 | Ridge Regression | — | — | — |
| 4 | Linear Regression | — | — | — |
| 5 | Decision Tree Regressor | — | — | — |

> The best regression model explains **87.9% of the variance** in monthly household income. Prediction error averages ₱3,929/month (MAPE: 20.42%), with higher-income households being harder to predict due to sparser training examples at the upper end of the distribution.

---

## How to Run

### 1. Clone the repository
```bash
git clone https://github.com/barcelonajames/philippine-fies-income-analysis.git
cd philippine-fies-income-analysis
```

### 2. Set up the environment
```bash
conda create -n fies-analysis python=3.11 -y
conda activate fies-analysis
pip install -r requirements.txt
```

### 3. Add the dataset
Download the FIES 2021 dataset from the [PSA website](https://psa.gov.ph/statistics/income-expenditure/fies) and place it in the project root:
```
philippine-fies-income-analysis/
└── Family_Income_and_Expenditure_edited.csv   ← place here
```

### 4. Open the notebook
```bash
jupyter notebook fies_income_analysis.ipynb
```
Or open it directly in VS Code with the Jupyter extension.

---

## Project Structure

```
philippine-fies-income-analysis/
├── fies_income_analysis.ipynb   ← Main notebook (run this)
├── requirements.txt             ← Python dependencies
├── .gitignore                   ← CSV and venv excluded
├── LICENSE                      ← MIT
└── README.md
```

---

## Tools & Libraries

| Category | Libraries |
|---|---|
| Data handling | pandas, numpy |
| Visualization | matplotlib, seaborn |
| Machine learning | scikit-learn, xgboost, lightgbm |
| Environment | Python 3.11, conda |

---

## Context

Built as part of the **Uplift Code Camp Python for Data and AI Bootcamp** (2026). The FIES dataset was chosen for its real-world policy relevance, the challenge of mixed data types across 64 features, and the opportunity to apply both classification and regression within a single pipeline on the same dataset.

---

*James Aleister Barcelona — Visual Designer & Data Analyst | Davao, Philippines*
