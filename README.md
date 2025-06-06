# Supervised ML Classifiers for Predicting Water Wells Condition

## 1. Project Overview

This project explores the use of supervised machine learning classifiers to predict the condition of water wells in Tanzania. By leveraging a ternary classification approach, the goal is to distinguish between wells that are functional, non-functional, or functional but in need of repair. The workflow encompasses data preprocessing, model building, evaluation, and actionable recommendations to support sustainable water resource management.

## 2. Business Understanding

Access to clean and reliable water is a critical challenge in Tanzania. Many wells fall into disrepair or become non-functional, impacting communities' health and livelihoods. Predicting the condition of water wells enables stakeholders to prioritize maintenance, allocate resources efficiently, and ensure long-term water access. This project addresses the question: **_Can supervised ML classification models trained on available data predict the operational status of a water-well in Tanzania ?_**

## 3. Data Preprocessing

The Data Preprocessing Pipeline encompases the following steps that are executed sequentially to prevent data-leakage:

1. Define Exog and Endog.
2. Perform Train-Test split.
3. Drop rendundant and irrelevant columns in **X_train**.
4. Handle missing values in **X_train**.
5. Feature engineering on **X_train**.
6. Multicollinearity check on numerical features in **X_train**.
7. Numerical Features' Normalization in **X_train**.
8. Categorical Features' OneHot Encoding in **X_train**.
9. Target Variable Label Encoding in **y_train**.
10. Address Class Imbalance in **y_train**
11. Preprocess Test set (**X_test** and **y_test**): Steps 3 to 9.
12. Preprocess Evaluation Data (**testdata.csv**) Steps 3 to 8.


## 4. Modelling

Multiple supervised ML classifiers are build, trained on a balanced training set, tuned, and their respective performance analyzed to determine the best-fit model for predicting values of a ternary target variable.

- **Decision Tree Classifier (baseline):** The baseline non-parametric model captures non-linear relationships and feature interactions. Hyperparameter tuning is implemented using **GridSearchCV** to optimize `max_depth`, `min_samples_split`, and `min_samples_leaf`.
- **Gradient Boosting Classifier:** The _Ensemble Boosting model_ combines multiple weak learners sequentially to improve performance. Hyperparameter tuning is performed using **GridSearchCV** to optimize `n_estimators`, `learning_rate`, `max_depth`, `subsample`, and `max_features`.
- **Random Forest Classifier:** The _Ensemble Bagging model_ builds indepedent/ parralel multiple decision trees to improve performance. Hyperparameter tuning is implemented via **GridSearchCV** to optimize `n_estimators`, `max_depth`, `min_samples_split`, and `max_features`.

## 5. Model Evaluation

### Confusion Matrices

**Gradient Boosting Classifier:**


**Random Forest Classifier:**


### ROC Curves

**Gradient Boosting Classifier:**




**Random Forest Classifier:**


### Performance Metrics
The predictive performance of the three classifiers on the test-set based on **_F1-score_**, and **_ROC-AUC_**.

| Model | F1-score (Train-set) | F1-score (Test-set) | Test ROC-AUC (Train-set) | Test ROC-AUC (Test-set) |
|---------|---------------|--------------|--------------|--------------|
| Decision Tree Classifier (tuned) | 0.998 | 0.756 | 1.0 | 0.756 |
| Gradient Boosting Classifier (tuned) | 0.876 | 0.777 | 0.971 | 0.889 |
| Random Forest Classifier (tuned) | 0. | 0. | 0. | 0. |

The prediction accuracy percentage of the three classifiers on the **_testdata.csv_** dataset.

| Model | Prediction Accuracy Percentage |
|---------|-----------------------|
| Decision Tree Classifier |  |
| Gradient Boosting Classifier |  |
| Random Forest Classifier |  |

**Selected Model for Deployment:** -The Hyperparameter-tuned Gradient Boosting Classifier consistently outperformed other models, achieving the highest F1-score (**_77.7%_**), ROC-AUC (**_88.9%_**). These metrics justify the classifier's balanced performance across all classes. The model's superirority is also justified by its comparatively higher prediction accuracy (70%) on the **_testdata.csv_** dataset. 


### Top 10 Important Features





## 6. Conclusion

The analysis demonstrates that tuned supervised ML models can effectively predict the condition of water wells using appropriately preprocessed features. The tuned Gradient Boosting Classifier is particularly a powerful, highly generalizable model that stakeholders in the Tanzanian water sector can leverage to to anticipate well failures and plan interventions proactively. 

## 7. Business Recommendations

- **Prioritize Maintenance:** Model predictions can be used to identify wells at risk and allocate maintenance resources efficiently.
- **Data Collection:** Continued improvement of data quality, especially for key features influencing well condition, is recommended.
- **Stakeholder Engagement:** Insights should be shared with local authorities and NGOs to inform decision-making and maximize impact.

## 8. Next Steps

- **Model Deployment:** Integration of the best-performing model into a user-friendly dashboard for real-time predictions and pilot target interventions high-risk areas/ water-well types.
- **Feature Expansion:** Incorporation of additional data sources (e.g., weather, usage patterns) to enhance model accuracy.
- **Continuous Monitoring:** Regular updates to the model with new data to maintain performance and relevance.


## 9. Repository Structure


├─ data

├── images

├── .gitignore

├── README.md

├── index.ipynb

├── notebook.pdf

└── presentation.pdf


