# Fintech AML Pipeline: Credit Card Fraud Detection

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Status](https://img.shields.io/badge/Status-Baseline%20Complete-green)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

## 📌 Project Overview
A robust machine learning pipeline for detecting fraudulent credit card transactions. This project focuses on handling **severe class imbalance** (0.17% fraud rate) and **financial outliers** in a privacy-preserving dataset.

The core challenge is the "Accuracy Paradox": A dummy model predicting "Legit" for everyone achieves 99.8% accuracy but catches **zero** fraud. This project prioritizes **Recall** (catching fraud) and **Precision** (minimizing false alerts) over raw accuracy.

## 📊 Key Results (Baseline Phase)
We established a strong baseline using **Weighted Logistic Regression** with probability threshold tuning.

| Model | Accuracy | Recall (Fraud Caught) | Precision (False Alarm Rate) | F1-Score |
|-------|----------|-----------------------|------------------------------|----------|
| **Dummy Classifier** | 99.83% | 0.00% | 0.00% | 0.00 |
| **LogReg (Standard)** | 99.92% | 65.31% | 83.12% | 0.73 |
| **LogReg (Tuned)** | **100.00%** | **81.63%** | **83.33%** | **0.82** |

> **Impact:** The optimized baseline catches **~82% of all fraud** while limiting false positives to just ~16 cases out of 56,000+ transactions.
<img width="1187" height="587" alt="image" src="https://github.com/user-attachments/assets/67807167-0bd5-41a5-9bc9-80869343c655" />


## 🏗️ Technical Architecture
* **Problem Type:** Binary Classification (Imbalanced)
* **Preprocessing:**
    * **RobustScaler:** Used on `Amount` and `Time` to mitigate the impact of extreme financial outliers.
    * **Log Transformation:** Applied to transaction amounts to normalize skewness.
* **Validation Strategy:** Stratified Train-Test Split to preserve fraud distribution.
* **Optimization:** Precision-Recall Curve analysis to find the optimal decision threshold (maximizing F1).

## 📂 Repository Structure
```text
fintech-aml-pipeline/
│
├── notebooks/
│   └── 01_baseline_pipeline.ipynb   # End-to-end: Data prep to Tuned Baseline
│
├── results/                         # Evaluation plots and metrics
│   └── baseline_comparison.png      # Performance visualization
│
├── src/                             # Modular production code (In Progress)
├── data/                            # Local data folder (Ignored by Git)
├── requirements.txt                 # Project dependencies
└── README.md                        # Documentation
```
## 🚀 Roadmap & Progress
- [x] **Phase 1: Pipeline Setup**
    - [x] Data Ingestion & Quality Checks
    - [x] Feature Engineering (Time-cycle & Log-amount)
    - [x] Leakage-Free Pipeline (Split before Scale)
- [x] **Phase 2: Baseline Modeling**
    - [x] Dummy Classifier (To expose Accuracy Paradox)
    - [x] Logistic Regression (Standard vs. Balanced)
    - [x] Threshold Tuning (Precision-Recall Optimization)
- [ ] **Phase 3: Advanced Modeling (Next)**
    - [ ] SMOTE / Undersampling Strategies
    - [ ] Random Forest & XGBoost Implementation
    - [ ] Hyperparameter Tuning

## 🛠️ Setup & Usage
1. **Clone the repo:**
   ```bash
   git clone https://github.com/Shamsun-Nahar-Nitu/fintech-aml-pipeline.git
   cd fintech-aml-pipeline
   
2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
3. **Get the Data:**
   * Download `creditcard.csv` from [Kaggle](https://www.kaggle.com/mlg-ulb/creditcardfraud).
   * Place it in the `data/` folder.

4. **Run the Notebook:**
   ```bash
   jupyter notebook notebooks/01_baseline_pipeline.ipynb
   ```
📧 Contact
For questions or collaboration, feel free to reach out or open an issue.
