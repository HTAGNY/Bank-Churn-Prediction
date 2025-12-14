# Bank Customer Churn Prediction

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Library](https://img.shields.io/badge/Library-Scikit--Learn%20|%20CatBoost%20|%20SHAP-orange)
![Status](https://img.shields.io/badge/Status-Completed-success)

> **Predicting customer attrition to optimize retention strategies.**

##  Project Notebook
 **[View the Notebook via NBViewer](https://nbviewer.org/github/HTAGNY/Bank-Churn-Prediction/blob/main/Bank_Project.ipynb)**  
*(Recommended for interactive plots that might not render on GitHub)*

---

##  Objective & Business Scope
Customer retention is crucial in the banking industry. Acquiring a new client is significantly more expensive than retaining an existing one.

The goal of this project is to:
1.  **Predict Churn:** Identify customers likely to close their accounts with high accuracy.
2.  **Understand Drivers:** Use interpretability tools (SHAP) to understand *why* customers leave.
3.  **Actionable Insights:** Provide a basis for a proactive retention system for the marketing team.

##  Methodology

We approached this as a binary classification problem on an **imbalanced dataset** (16% churners vs 84% retained).

1.  **Exploratory Data Analysis (EDA):** Identification of patterns and handling of class imbalance.
2.  **Feature Engineering:** Creation of behavioral ratios (e.g., `Avg_Trans_Value`, `Inactive_Ratio`) to enhance model predictive power.
3.  **Model Selection:** Testing simple baselines vs. advanced ensemble methods.
4.  **Optimization:** Using GridSearch and dealing with imbalance via class weights rather than synthetic oversampling (SMOTE).
5.  **Interpretability:** Using SHAP values to explain predictions.

## Models Tested

We evaluated a wide range of algorithms, from bagging to boosting:
*   **Baselines:** Logistic Regression, Decision Tree
*   **Ensemble Methods:** Random Forest, Bagging Classifier
*   **Boosting Algorithms:** Gradient Boosting, XGBoost, **CatBoost**
*   **Meta-Models:** Voting Classifier, Stacking Classifier

##  Key Results

The models were evaluated based on **F1-Score** and **Recall** (to minimize missed churners), rather than just Accuracy.

| Model | Accuracy | F1-Score | ROC-AUC |
| :--- | :---: | :---: | :---: |
| **CatBoost (Best)** | **97.3%** | **0.91** | **0.99** |
| Stacking | 97.2% | 0.91 | 0.99 |
| Voting Classifier | 97.2% | 0.91 | 0.99 |
| Random Forest | 95.5% | 0.85 | 0.98 |

**Why CatBoost?**
It provided the best balance between Precision and Recall, handled categorical features natively, and offered robust performance without overfitting.

##  Business Insights (SHAP Analysis)
Our analysis revealed the top indicators of churn:
1.  **Transaction Frequency (`Total_Trans_Ct`):** The strongest predictor. A sharp drop in activity is a major red flag.
2.  **Revolving Balance:** Surprisingly, customers with **zero** credit card debt are more likely to churn (less financial "stickiness").
3.  **Transaction Value:** Customers with smaller basket sizes are at higher risk.

---

##  Installation & Usage

1.  Clone the repo:
    ```bash
    git clone https://github.com/HTAGNY/Bank-Churn-Prediction.git
    ```
2.  Install dependencies:
    ```bash
    pip install pandas numpy scikit-learn matplotlib seaborn xgboost catboost shap
    ```
3.  Run the notebook using Jupyter Lab or Notebook.

##  Authors
*   Harold TAGNY
*   Sandy TEFOUEGOUM
*   Alida Dovila ZOGO
