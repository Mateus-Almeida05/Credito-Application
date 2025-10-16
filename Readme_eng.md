<img width="373" height="390" alt="image" src="https://github.com/user-attachments/assets/553f4241-0bb0-43d7-b8d7-4844263d84d3" />

# **Credit Model \- Application Score**
 
## **1\. Introduction**

This project aims to develop a predictive credit model capable of estimating the probability of customer default based on their registration data, financial history, and payment behavior records.

The initiative seeks to build a credit scoring model (Application Score) that can be consistently applied to support decisions related to credit granting, limit reviews, and credit risk management.

## **2\. Problem Solved**

In the context of credit analysis and approval, financial institutions face a recurring challenge: accurately and proactively identifying which customers are more likely to default. Decisions based only on limited history, analyst perception, or manual criteria tend to be inconsistent and often result in significant financial losses—either by approving high-risk clients or rejecting good payers.

Given this scenario, the project proposes creating a statistical model capable of automatically assessing the credit risk of new applicants, using large volumes of historical and behavioral data to assign a probability of default (score) to each client. This model enables the construction of a more rational and data-driven credit policy, reducing subjectivity in decision-making and improving process efficiency.

The main objective is to balance risk and return, ensuring that credit is granted sustainably. To achieve this, the model must not only accurately identify potential defaulters but also remain stable and interpretable, allowing it to be audited and transparently used by risk, compliance, and business teams.

In addition to reducing delinquency, the model also enables customer segmentation by risk profile, allowing differentiated strategies for pricing, credit limits, and post-loan monitoring. In this way, the institution can improve profitability and strengthen risk control using a reliable analytical tool easily integrated into decision systems.

## **3\. Problem-Solving Approach**

The development of the model was divided into sequential stages, from data exploration to final performance evaluation:

i) **Data Collection and Understanding:** Different datasets related to credit applications, banking history, card balances, payments, and previous contracts were used.

ii) **Data Cleaning and Processing:**

* Standardization of variable names and types

* Removal of missing values and inconsistencies

* Creation of temporal flags and derived variables

iii) **Feature Engineering:**

* Aggregations by customer (SK\_ID\_CURR) across multiple sources (e.g., bureau, previous applications, installments, POS\_CASH)

* Creation of behavioral indicators (mean, sum, delay, payment variation)

* Application of supervised discretization techniques using decision trees and transformation of continuous variables

iv) **Feature Selection:**

* Analysis of variable completeness and correlations

* Removal of collinear and redundant variables

* Assessment of linearity with log(odds) and application of mathematical transformations

* Retention of only significant variables (p ≤ 0.05)

v) **Modeling:**

* Training of baseline models with different algorithms (Decision Tree, Random Forest, Gradient Boosting, LightGBM, and Logistic Regression)

* Final choice of the Logistic Regression model due to its interpretability and consistent performance

vi) **Evaluation and Validation**:

* Metrics used: KS, AUC-ROC, and Gini Index

* Stability analysis between training and test datasets

* Creation of a scorecard and ranking curve by decile

vii) **Model Export and Saving:**

* The final model was saved in .pkl format along with the encoder and selected variables, ensuring process reproducibility.

## **4\. Project Structure**

Modelo\_Credito\_Application/  
├── 00-Conjunto\_de\_Dados/               \# Folder containing the original datasets used in the analysis  
├── 01-Conjunto\_de\_Dados\_Tratados/      \# Processed and aggregated datasets after cleaning and standardization  
├── 02-Feature\_Engineering/             \# Notebooks and scripts for feature engineering and new attribute creation  
├── 03-Feature\_Selection\_Base\_Full/     \# Variable selection stage, correlation and linearity analysis  
├── 04-Modelos/                         \# Machine learning models tested and the final logistic regression model  
└── README.md                           \# Project documentation and description of the modeling pipeline

## **5\. Technology Used**

* Language: Python  
* Data Manipulation: pandas, numpy  
* Statistical Analysis: statsmodels, scipy  
* Machine Learning: scikit-learn, LightGBM, XGBoost  
* Visualization: matplotlib, seaborn  
* Feature Engineering: category\_encoders, DecisionTreeClassifier, TargetEncoder


## **6\. Results**

The results showed that the model demonstrated good stability and high discriminatory power across the training and testing datasets, confirming its generalization capability and consistent performance. Evaluation metrics (KS, AUC-ROC, and Gini) indicated a model capable of accurately distinguishing high- and low-risk clients, with no signs of overfitting. The decile analysis confirmed the consistency of the risk curve, with higher default rates in lower deciles and decreasing along the score range, highlighting the model’s ability to rank customers correctly by credit risk.

Logistic Regression was chosen as the final model because it combines performance, interpretability, and robustness—essential characteristics in credit contexts, where understanding and justifying decisions is crucial. Its statistical structure allows for analyzing the sign and importance of each variable, facilitating score interpretation and integration into corporate decision systems.

In summary, the project delivered a reliable, interpretable, and validated credit model built from a complete pipeline of data processing, feature engineering, and statistical modeling. The adopted methodology is flexible and can be applied to different credit products and segments, helping to reduce delinquency, optimize lending policies, and support strategic decision-making based on solid and transparent data.

