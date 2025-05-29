<!--
  IFRS 9 ECL Modeling Project
  Author: OSSE Daniel
  Date: May 29, 2025
-->

<p align="center">
  <img src="https://img.shields.io/badge/Project-IFRS9-blue" alt="Project Badge">
  <img src="https://img.shields.io/badge/Status-Completed-brightgreen" alt="Status Badge">
</p>

# 🧮 IFRS 9 – Expected Credit Loss (ECL) Modeling

A professional end-to-end project to simulate and compute Expected Credit Loss in accordance with IFRS 9 using the German Credit dataset. This includes PD, LGD, EAD modeling, scenario analysis, and staging classification.

---

# 📘 Modeling Expected Credit Loss (ECL) under IFRS 9

**Author:** OSSE Daniel  
**Date:** May 29, 2025  
**Data:** German Credit Dataset (1,000 borrowers)

---

## 🧩 1. Introduction

This project aims to model **Expected Credit Loss (ECL)** in compliance with the **IFRS 9** standard. The analysis is based on a dataset containing socio-economic and financial information for 1,000 German borrowers.

---

## 🎯 2. Project Objectives

- Predict the **Probability of Default (PD)** using statistical models.
- Estimate **Loss Given Default (LGD)** and **Exposure at Default (EAD)**.
- Apply the **IFRS 9 staging logic** (Stage 1, 2, 3).
- Compute ECL under different **economic scenarios**.
- Generate **individual credit scores** to rank portfolio risk.

---

## 📊 3. Data Description

- **Source**: German Credit dataset (20 variables: 7 numerical, 13 categorical)
- **Target**: Binary default risk (0 = good client, 1 = bad client)

---

## 🔍 4. PD Modeling

- **Models trained**:
  - Logistic Regression (weighted + SMOTE)
  - Decision Tree Classifier
  - Random Forest Classifier
  - Gradient Boosting Classifier
- **Selected model**: Logistic Regression with SMOTE + class weighting
- **AUC Score**: **0.74**
- **Accuracy**: **0.73**
- **Recall**: **0.67**
- **Outputs**:
  - ROC Curve
  - Confusion matrix
  - Variable importance
  - **Probability-based scoring** for staging and risk ranking

---

## 💸 5. LGD Modeling

- **Models trained**:
  - Linear Regression
  - Ridge Regression
  - Random Forest Regressor
  - Gradient Boosting Regressor
- **Selected model**: Gradient Boosting Regressor
- **Average predicted LGD**: **0.46**
- **Evaluation**:
  - R² = 0.6012
  - Std R² = 0.0742
- **Outputs**:
  - Predicted LGD per contract

---

## 🏦 6. EAD Modeling

- **Models trained**:
  - Linear Regression on CCF
  - Gradient Boosting Regressor on Drawn/Limit
- **Approach**: Simulation of drawn amount and credit limit
- **Simulated CCF**: Average of **0.40**
- **Average EAD**: **3,393 €**
- **Outputs**:
  - Drawn vs Limit plots
  - Regression diagnostics

---

## ⚙️ 7. IFRS 9 Staging

- **Stage 1**: Exposures with no significant credit risk increase
- **Stage 2**: PD >= 20%
- **Stage 3**: Observed default
- **Score thresholds**: used to classify staging based on predicted PD

---

## 🌐 8. Economic Scenarios

| Scenario    | Weight | Applied shocks (PD, LGD, EAD)     |
|-------------|--------|-----------------------------------|
| Baseline    | 50 %   | (1.00, 1.00, 1.00)                |
| Adverse 1   | 20 %   | (1.20, 1.10, 1.00)                |
| Adverse 2   | 20 %   | (1.30, 1.15, 1.05)                |
| Severe      | 10 %   | (1.50, 1.25, 1.10)                |

---

## 📈 9. Final Results – Version – Lifetime Discounting + Scenario Weighting

- **ECL distribution by stage in proportion of credit limit**:

| Stage   | Total ECL (DM) | Credit Limit (DM) | % ECL / Credit Limit |
|---------|----------------|-------------------|----------------------|
| Stage 1 | 43,912         | 698,242           | 6.29%                |
| Stage 2 | 413,789        | 1,892,778         | 21.86%               |
| Stage 3 | 401,461        | 1,470,142         | 27.31%               |

---

## 🧾 10. Conclusion

This project implements a full IFRS 9 ECL modeling framework. It can be generalized to real portfolios with multi-period histories and enriched with advanced macroeconomic features.
