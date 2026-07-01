# 📊 Telecom Customer Churn — Data Analysis Project

An end-to-end **data analysis project** that explores telecom customer churn — covering data cleaning, exploratory data analysis (EDA), feature correlation analysis, and predictive modeling as a supporting step, culminating in actionable business insights and recommendations.

![Python](https://img.shields.io/badge/Python-3.12-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Wrangling-150458)
![Scikit--learn](https://img.shields.io/badge/Scikit--learn-ML-F7931E)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

---

## 🎯 Project Objective

Analyze telecom customer data to uncover the structural and behavioral indicators driving customer churn. This involves establishing a clean data feed through systematic typecasting, outlier isolation, and correction of blank/inconsistent values, then using statistical and visual analysis to surface the patterns behind why customers leave — with a lightweight predictive model included to validate and rank those findings.

## 🗂️ Dataset

| | |
|---|---|
| **Source** | [Kaggle Telecom Customer Churn dataset](https://www.kaggle.com/) (`WA_Fn-UseC_-Telco-Customer-Churn.csv`) |
| **Records** | 7,043 customer accounts |
| **Features** | 21 attributes — demographics, account/engagement data, subscribed services, and billing information |
| **Target** | `Churn` (Yes / No) |

**Feature groups:**
- **Identity** — `customerID`
- **Demographic** — `gender`, `SeniorCitizen`, `Partner`, `Dependents`
- **Engagement** — `tenure`, `Contract`, `PaperlessBilling`
- **Services** — `InternetService`, `OnlineSecurity`, `TechSupport`, `StreamingTV`, `StreamingMovies`, etc.
- **Financials** — `MonthlyCharges`, `TotalCharges`, `PaymentMethod`

---

## 🛠️ Tech Stack

| Component | Tools |
|---|---|
| Environment | Python 3.12, Jupyter Notebook |
| Data Handling | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Statistical/Predictive Check | Scikit-learn |
| Model Persistence | Joblib |

---

## 🔄 Pipeline Overview

```
Raw CSV (7043 × 21)
      │
      ▼
1. Data Cleaning        → fix TotalCharges type, impute nulls, dedupe
      │
      ▼
2. Exploratory Analysis → churn distribution, tenure/billing trends, categorical breakdowns
      │
      ▼
3. Feature Encoding     → drop customerID, label-encode categoricals, train/test split
      │
      ▼
4. Predictive Check     → Logistic Regression, Decision Tree, Random Forest (validates the analysis)
      │
      ▼
5. Driver Ranking       → identify top churn drivers
      │
      ▼
6. Business Insights    → retention recommendations
```

### 1. Data Cleaning
- Loaded raw dataset — shape `(7043, 21)`, zero nulls detected in the initial check.
- Found **11 blank-space entries** hidden in `TotalCharges` (stored as text), invisible to a standard null check.
- Converted `TotalCharges` to numeric with `pd.to_numeric(..., errors="coerce")`.
- Imputed the resulting NaNs using the **column median**.
- Verified zero duplicate records and exported `cleaned_telco_churn.csv`.

### 2. Exploratory Data Analysis
- **Class balance:** 5,174 retained (73.5%) vs. 1,869 churned (26.5%) — a ~3:1 imbalance.
- **Tenure vs. billing:**

  | Segment | Avg. Tenure | Avg. Monthly Charges |
  |---|---|---|
  | Churned | 17.9 months | $74.40 |
  | Active | 37.6 months | $61.30 |

- Explored Gender, Senior Citizen, Partner/Dependents, and Contract type vs. Churn.

**Key insights:**
- Month-to-month customers churn more than longer-contract customers.
- Longer tenure correlates with loyalty.
- Higher monthly charges increase churn risk.
- Tech Support subscribers churn less.
- Electronic Check payers churn more than other payment methods.

### 3. Feature Encoding
- Dropped non-predictive `customerID`.
- Label-encoded all categorical columns for correlation analysis.
- Split into `X` (7043 × 19) / `y` (`Churn`).
- 80/20 stratified split → **5,634 / 1,409** records (used to sanity-check the analysis in step 4).

**Top correlations with Churn:**

| Feature | Correlation |
|---|---|
| Contract | −0.397 |
| tenure | −0.352 |
| OnlineSecurity | −0.289 |
| TechSupport | −0.282 |
| TotalCharges | −0.199 |
| MonthlyCharges | +0.193 |
| PaperlessBilling | +0.192 |

### 4. Predictive Check

To validate that the patterns found during EDA actually hold up, three simple classifiers were trained and evaluated on a held-out test set:

| Model | Accuracy | Precision | Recall | F1-Score |
|---|---|---|---|---|
| **Logistic Regression** ⭐ | **80.27%** | 0.646 | 0.570 | 0.605 |
| Random Forest | 79.21% | 0.637 | 0.503 | 0.562 |
| Decision Tree | 73.03% | 0.492 | 0.519 | 0.505 |

Logistic Regression performed best (80.27% accuracy), confirming that the relationships surfaced in EDA — contract type, tenure, billing amounts — are genuinely predictive of churn, not just correlational noise.

### 5. Churn Driver Ranking (via Random Forest)

| Rank | Feature | Importance |
|---|---|---|
| 1 | TotalCharges | 0.1868 |
| 2 | MonthlyCharges | 0.1792 |
| 3 | tenure | 0.1543 |
| 4 | Contract | 0.0796 |
| 5 | PaymentMethod | 0.0501 |
| 6 | OnlineSecurity | 0.0496 |
| 7 | TechSupport | 0.0436 |
| 8 | gender | 0.0279 |
| 9 | InternetService | 0.0278 |
| 10 | OnlineBackup | 0.0271 |

Billing fields (`TotalCharges`, `MonthlyCharges`) and `tenure` together account for over half of the driver weight — reinforcing the correlation and EDA findings above.

---

## 💡 Business Recommendations

1. **Promote long-term contracts** — migrate month-to-month customers to annual plans.
2. **Target retention offers** at high-risk, newer, higher-billed accounts.
3. **Strengthen technical support** — subscribers churn less.
4. **Rebalance pricing** for high-monthly-charge customers.
5. **Build tenure-based loyalty programs.**
6. **Monitor and proactively engage** customers matching the high-risk profile identified in the analysis.

---

## 📁 Repository Structure

```
├── dataset/
│   └── WA_Fn-UseC_-Telco-Customer-Churn.csv
├── cleaned_telco_churn.csv
├── X_train.csv / X_test.csv
├── y_train.csv / y_test.csv
├── feature_importance.csv
├── random_forest_model.pkl
├── CODING.ipynb
└── README.md
```

## 🚀 Getting Started

```bash
# Clone the repository
git clone https://github.com/<your-username>/telecom-customer-churn.git
cd telecom-customer-churn

# Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn joblib

# Run the notebook
jupyter notebook CODING.ipynb
```

## 📈 Next Steps

- Segment churn analysis further by tenure cohort and service bundle.
- Address class imbalance (26.5% churners) with weighted metrics or SMOTE if the predictive check is extended.
- Build a recurring dashboard to track churn drivers over time.
- Share findings with the retention team to prioritize the segments flagged above.

