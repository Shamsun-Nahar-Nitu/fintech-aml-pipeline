## Fintech AML Pipeline: Credit Card Fraud Detection

### 📌 Project Overview
A robust machine learning pipeline for detecting fraudulent credit card transactions. This project focuses on handling **severe class imbalance** (0.17% fraud rate) and **financial outliers** in a privacy-preserving dataset.

### 🏗️ Technical Architecture
* **Problem Type:** Binary Classification (Imbalanced)
* **Preprocessing:**
    * **RobustScaler:** Used on `Amount` and `Time` to mitigate the impact of extreme financial outliers.
    * **Log Transformation:** Applied to transaction amounts to normalize skewness.
* **Validation Strategy:** Stratified Train-Test Split to preserve fraud distribution.

## 📂 Repository Structure
```text
├── notebooks/          # Step-by-step analysis and modeling
│   └── 01_data_prep_pipeline.ipynb
├── src/                # Modular code for production (In Progress)
├── requirements.txt    # Project dependencies
└── README.md
