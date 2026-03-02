# Predictive Business Intelligence: E-Commerce Churn Analysis
**Author:** Daniel Mendonça  
**Stack:** SQL (BigQuery), Python (XGBoost, Scikit-Learn), Google Cloud Platform  
**Framework:** PACE (Plan, Analyze, Construct, Execute)

## 🎯 Project Overview
This project addresses a critical business challenge: **Customer Retention**. Using the Google BigQuery `thelook_ecommerce` public dataset, I built a predictive system to identify customers likely to churn (defined as no purchase activity for 60+ days). 

By identifying these users proactively, a business can transition from reactive revenue loss to proactive, data-driven retention strategies.



## 🛠️ Technical Architecture
Following the **PACE framework** popularized by the Google Advanced Data Analytics Professional Certificate:

1.  **Plan:** Defined the business problem and established the **F1-Score** as the primary metric to balance the cost of false alarms (unnecessary discounts) against the cost of lost customer lifetime value (LTV).
2.  **Analyze:** * Extracted data using complex **BigQuery SQL** (CTEs and relational joins).
    * Performed Exploratory Data Analysis (EDA) to identify severe class imbalance.
    * Analyzed feature correlations and data distributions.
3.  **Construct:**
    * Engineered behavioral features: Account Tenure, Total Spend, and Traffic Source.
    * Built a robust preprocessing pipeline using `ColumnTransformer` and `RobustScaler`.
    * Conducted hyperparameter tuning via `GridSearchCV` for both **Random Forest** and **XGBoost**.
4.  **Execute:** Evaluated the "Champion" model using Confusion Matrices and Feature Importance analysis to deliver actionable business recommendations.

## 📊 Key Results
* **Best Model:** Tuned XGBoost (optimized for F1-score).
* **Key Churn Drivers:** Account Tenure and Total Spend were the strongest indicators of risk.
* **Retention Insight:** Users who do not return within 15 days of their first order have a **40% higher probability of churn**.



## 💡 Business Recommendations
* **Automation:** Integrate the XGBoost model into the marketing stack to trigger automated "re-engagement" sequences for users crossing the 50% churn probability threshold.
* **First-Week Engagement:** Implement a loyalty milestone reward for users hitting their 14-day mark to stabilize early-stage churn.
* **Marketing Audit:** Audit the 'Facebook Ads' channel, as it exhibits a disproportionately higher churn rate compared to organic traffic, suggesting a misalignment in customer expectations.

## ⚖️ Ethical Considerations
* **Bias Mitigation:** Personally Identifiable Information (PII) was excluded to ensure the model focuses on behavioral patterns rather than demographic identity.
* **Transparency:** The model is strictly intended for positive interventions (discounts, rewards) rather than punitive actions.

## 🚀 How to Run
1. Clone this repository.
2. Ensure you have a Google Cloud Project with BigQuery access.
3. Install dependencies: `pip install google-cloud-bigquery pandas scikit-learn xgboost seaborn`.
4. Update the `project_id` in the notebook to your GCP Project ID.
