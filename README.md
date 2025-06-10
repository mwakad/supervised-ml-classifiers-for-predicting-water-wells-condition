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
![confusion-matrices-gradient-boosting-classifier](https://github.com/user-attachments/assets/621c1a9f-d517-4910-b27e-f793b6a87210)

**Random Forest Classifier:**
![confusion-matrices-random-forest-classifier](https://github.com/user-attachments/assets/6a633814-8d70-4ff4-8dbe-1a5944b36732)


### ROC Curves

**Gradient Boosting Classifier:**

![roc-curves-gradient-boosting-classifier](https://github.com/user-attachments/assets/66497f92-1dba-4f92-a25c-cbca5ef3c895)

**Random Forest Classifier:**
![roc-curves-random-forest-classifier](https://github.com/user-attachments/assets/024d9ea8-8291-4d4a-87a0-81178420b471)


### Performance Metrics
The predictive performance of the three classifiers on the test-set based on **_F1-score_**, and **_ROC-AUC_**.

| Model | F1-score (Train-set) | F1-score (Test-set) | Test ROC-AUC (Train-set) | Test ROC-AUC (Test-set) |
|---------|---------------|--------------|--------------|--------------|
| Decision Tree Classifier (tuned) | 0.998 | 0.756 | 1.0 | 0.756 |
| Gradient Boosting Classifier (tuned) | 0.876 | 0.777 | 0.971 | 0.889 |
| Random Forest Classifier (tuned) | 0.972 | 0.791 | 0.999 | 0.900 |

The prediction accuracy percentage of the three classifiers on the **_testdata.csv_** dataset.

| Model | Prediction Accuracy Percentage |
|---------|-----------------------|
| Decision Tree Classifier | 67.54% |
| Gradient Boosting Classifier | 71.06% |
| Random Forest Classifier | 70.77% |

**Selected Model for Deployment:** Although the **_Random Forest Classifier_** outperforms the other models across the three performace metrics (_Accuracy_, _F1-score_, and _ROC-AUC_); the **_Gradient Boosting Classifier_** is selected for deployment. This is because the gap between the **_Gradient Boosting Classifier's_** performance metrics on the train-set Vs. on the test-set is the least for the model. The **_Gradient Boosting Classifier's_** superiority and generalizability to this ternary classification problem is justified by its comparatively higher prediction accuracy (**71.06%**) on the **_testdata.csv_** dataset. 


### Top 10 Important Features

![important-features](https://github.com/user-attachments/assets/6c4c9000-b26e-4754-abe8-39b1512dc18f)


## 6. Conclusion

The analysis demonstrates that tuned supervised ML models can effectively predict the condition of water wells using appropriately preprocessed features. The tuned Gradient Boosting Classifier is particularly a powerful, highly generalizable model that stakeholders in the Tanzanian water sector can leverage to to anticipate well failures and plan interventions proactively. 

## 7. Business Recommendations

- **Prioritize Maintenance:** Model predictions can be used to identify wells at risk and allocate maintenance resources efficiently.
- **Data Collection:** Continously improve the training dataset's quality by collecting more data on the key important features, and ensuring variable's labels/ values are recorded accurately.
- **Stakeholder Engagement:** Insights deduced from this project should be shared with local authorities, other NGOs involved in public service and the Tanzanian Government representatives to support data-driven decision-making.

## 8. Next Steps

- **Model Deployment:** Integration of the hyperparameter-tuned **_Gradient Boosting Classifier_** into a user-friendly dashboard for real-time predictions and leveraging the model's predicitions to pilot target interventions.
- **Feature Expansion:** Incorporate additional features such as weather data and a water-well's usage patterns) to enhance model accuracy.
- **Continuous Monitoring:** Formulate and implement frameworks for updating the model's training dataset with recent/ latest data to improve the classifier's performance.


## 9. Repository Structure


├─ data

├── images

├── .gitignore

├── README.md

├── index.ipynb

├── notebook.pdf

└── presentation.pdf


