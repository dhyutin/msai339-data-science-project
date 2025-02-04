# Bridging the Gap: Analyzing Pay Disparities Across Industries

## MSAI 339 - Final Project Report  
**Team Name:** Powerpuff Girls  
**Contributors:** Sree Dhyuti Nimmagadda, Shruti Kalaskar, Divyanka Thankur, Ruchi Bommaraju  
**Professor:** Dr. Joshua D’Arcy  

## Introduction  
Pay parity is essential for workplace equality, yet disparities persist due to factors like gender, industry, education, and regional differences. This project explores pay disparity using data science methods to analyze salary correlations and predict salary trends while addressing data-induced biases.

## Dataset  
We used Kaggle’s **Gender Pay Gap Dataset (1980–2013)** sourced from the **U.S. Census Bureau** and **Bureau of Labor Statistics (BLS)**. It includes ~350,000 data points covering demographics, employment, education, income, and location.

## Data Preprocessing  
- Dropped irrelevant/redundant columns.
- Applied **hypothesis testing** for feature selection.
- Handled missing values using **multiple imputations**.
- Reduced dataset size from **34M+ rows × 228 columns** to **344K rows × 31 columns**.

## Exploratory Data Analysis (EDA)  
- Gender differences are primarily observed in salary values.
- Existing models predict **lower salaries for females** despite similar qualifications.
- There's a strong need for **bias-aware salary prediction models**.

## Modeling  

### Model Selection  
We experimented with **boosting algorithms** for salary prediction. The best-performing model was **LightGBM**:

| ML Model                | RMSE      | MAE       | R² Score |
|-------------------------|----------|-----------|----------|
| XGBoost                | 34,198.12 | 14,950.83 | 0.410    |
| Gradient Boosting      | 34,257.18 | 15,008.85 | 0.408    |
| Lasso Regression       | 36,950.87 | 17,912.84 | 0.350    |
| Ridge Regression       | 36,948.75 | 17,912.44 | 0.380    |
| **LightGBM**          | **34,184.06** | **16,166.49** | **0.459** |

### Model Improvement  
We improved **LightGBM** by iteratively boosting residuals, resulting in **significant performance gains**:

- **Initial Validation:**
  - RMSE: **34,184.06** → Improved: **18,962.79**
  - MAE: **16,166.49** → Improved: **10,985.72**
  - R² Score: **0.459** → Improved: **0.8208**

## Error Quantification & Bias Analysis  
- We **reversed gender labels** to observe model biases.
- Results showed **salary discrepancies based on gender alone**.
- Example (Gradient Boosting):
  - **Original Male Prediction:** $47,806.85$
  - **Altered Male Prediction:** $31,453.21$
  - **Original Female Prediction:** $31,453.21$
  - **Altered Female Prediction:** $47,806.85$

### Mitigating Gender Bias  
1. **Reversed gender labels** to assess prediction shifts.  
2. **Calculated residuals** between original and altered salary predictions.  
3. **Refined models** using fairness-aware learning strategies.

## Conclusion  
Our study highlights persistent **gender-based salary disparities** and how traditional ML models **reinforce biases**. Key takeaways:  
- **LightGBM with residual learning** effectively improves salary predictions.  
- **Gender bias persists** and requires targeted mitigation strategies.  
- Future work includes **fairness-aware ML models** and dataset expansion to other industries/regions.

## References  
1. Blau, F.D., & Kahn, L.M. (2017). The gender wage gap: Extent, trends, and explanations. *Journal of Economic Literature, 55*(3), 789-865.  
2. Friedman, J.H. (2001). Greedy function approximation: A gradient boosting machine. *Annals of Statistics, 29*(5), 1189-1232.  
3. World Economic Forum. (2023). *Global Gender Gap Report 2023*. [Link](https://www.weforum.org/publications/global-gender-gap-report-2023)  

---

📌 **Repository Guide**  
- `/data`: Raw and processed datasets.  
- `/notebooks`: Jupyter notebooks for analysis and model development.  
- `/models`: Trained ML models and evaluation metrics.  
- `/reports`: Project documentation and final report.  

🚀 **Contributions & Feedback**  
Feel free to raise issues or suggest improvements via pull requests!  
