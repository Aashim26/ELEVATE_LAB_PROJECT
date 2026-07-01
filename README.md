# 📊 Telecom Customer Churn Analysis

An end-to-end Data Analyst project that analyzes telecom customer churn using Python, SQL concepts, Exploratory Data Analysis (EDA), and Machine Learning to identify customers who are likely to leave the company.

---

## 📌 Project Overview

Customer churn is one of the biggest challenges in the telecom industry. This project analyzes customer behavior and builds predictive machine learning models to identify customers at risk of churning.

The project includes:

- Data Cleaning & Preprocessing
- Exploratory Data Analysis (EDA)
- Feature Engineering
- Machine Learning Model Building
- Model Evaluation
- Business Insights & Recommendations

---

## 🎯 Objective

The main objective is to:

- Analyze customer behavior
- Identify factors affecting churn
- Build a predictive machine learning model
- Provide business recommendations to reduce customer churn

---

## 📂 Dataset

- **Dataset:** Telecom Customer Churn Dataset
- **Source:** Kaggle
- **Records:** 7,043 Customers
- **Features:** 21 Columns

Dataset includes:

- Customer Demographics
- Subscription Details
- Internet Services
- Payment Information
- Contract Details
- Churn Status

---

## 🛠️ Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Joblib

---

## 📈 Project Workflow

### 1️⃣ Data Collection

- Imported Telecom Customer Churn dataset
- Inspected data structure

### 2️⃣ Data Cleaning

- Removed inconsistencies
- Converted data types
- Handled missing values
- Removed duplicates

### 3️⃣ Exploratory Data Analysis (EDA)

- Churn Distribution
- Monthly Charges Analysis
- Contract Type Analysis
- Tenure Analysis
- Correlation Analysis
- Feature Relationships

### 4️⃣ Feature Engineering

- Label Encoding
- Feature Selection
- Train-Test Split

### 5️⃣ Machine Learning Models

Models trained:

- Logistic Regression
- Decision Tree Classifier
- Random Forest Classifier

---

## 📊 Model Performance

| Model | Accuracy |
|--------|----------|
| Logistic Regression | **80.27%** |
| Random Forest | 79.21% |
| Decision Tree | 73.03% |

🏆 **Best Performing Model:** Logistic Regression

---

## 🔍 Key Insights

- Customers with month-to-month contracts are more likely to churn.
- Higher monthly charges increase churn risk.
- Longer customer tenure reduces churn.
- Customers using Tech Support churn less frequently.
- Electronic Check payment users have higher churn rates.

---

## 💡 Business Recommendations

- Promote long-term contracts.
- Improve customer retention programs.
- Offer discounts to high-risk customers.
- Encourage Tech Support subscriptions.
- Build loyalty programs for long-term customers.

---

## 📁 Project Structure

```
Telecom-Customer-Churn/
│
├── dataset/
│   ├── WA_Fn-UseC_-Telco-Customer-Churn.csv
│
├── notebooks/
│   ├── Telecom_Customer_Churn.ipynb
│
├── reports/
│   ├── Telecom_Customer_Churn_Report.pdf
│
├── models/
│   ├── random_forest_model.pkl
│
├── images/
│   ├── churn_distribution.png
│   ├── feature_importance.png
│   ├── correlation_heatmap.png
│
├── README.md
└── requirements.txt
```

---

## 🚀 Future Improvements

- Hyperparameter Tuning
- SMOTE for Class Imbalance
- XGBoost & LightGBM Models
- Deploy using Streamlit or Flask
- Real-time Customer Churn Prediction

---

## 📷 Sample Outputs

- Customer Churn Distribution
- Correlation Heatmap
- Feature Importance
- Confusion Matrix
- Model Accuracy Comparison

---

## 👨‍💻 Author

**Vineeth Kumar**

Aspiring Data Analyst

### Skills

- Python
- SQL
- Power BI
- Excel
- Machine Learning
- Data Visualization
- Exploratory Data Analysis

---

## ⭐ If you found this project useful,

Please consider giving it a ⭐ on GitHub!
