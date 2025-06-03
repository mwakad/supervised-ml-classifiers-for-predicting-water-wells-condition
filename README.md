# Supervised ML Classifiers for Predicting Water Wells Condition

## 1. Project Overview

This project explores the use of supervised machine learning classifiers to predict the condition of water wells in Tanzania. By leveraging a ternary classification approach, the goal is to distinguish between wells that are functional, non-functional, or functional but in need of repair. The workflow encompasses data preprocessing, model building, evaluation, and actionable recommendations to support sustainable water resource management.

## 2. Business Understanding

Access to clean and reliable water is a critical challenge in Tanzania. Many wells fall into disrepair or become non-functional, impacting communities' health and livelihoods. Predicting the condition of water wells enables stakeholders to prioritize maintenance, allocate resources efficiently, and ensure long-term water access. This project addresses the question: **Can the operational status of water wells be accurately predicted using available data and machine learning?**

## 3. Data Preprocessing

The Data Preprocessing Pipeline encompases the followig steps that are executed sequentially to prevent data-leakage:

1. Define Exog and Endog.
2. Perform Train-Test split.
3. Drop rendundant and irrelevant columns.
4. Hande missing values.
5. Feature engineering.
6. Multicollinearity check on numerical features.
7. Numerical Features' normalization.
8. Categorical Features' OneHot Encoding.
9. Target Variable Label Encoding.
10. Addressing Class Imbalance in X_train
11. Preprocessing Test Data.
12. Preprocessing Validation Data


## 4. Modelling

Multiple supervised ML classifiers are build, trained on a balanced training set, tuned, and their respective performance analyzed to determine the best-fit model for predicting values of a ternary target variable.

- **Logistic Regression (Baseline):** Serves as a simple, interpretable benchmark for multiclass classification. Both untuned and hyperparameter-tuned versions were evaluated.
- **Decision Tree Classifier:** Captures non-linear relationships and feature interactions. The model is optimized through grid search, adjusting parameters such as tree depth and minimum samples per split.
- **Gradient Boosting Classifier:** Ensemble learning is leveraged to combine multiple weak learners for improved accuracy. Hyperparameter tuning is performed to optimize the number of estimators, learning rate, and tree depth.

Model selection and tuning are guided by cross-validation and grid search to identify the best-performing configurations for each classifier.

## 5. Model Evaluation

### Confusion Matrices
They capture the counts of a model's True Positives, True Negatives, False Positive, and False Negatives. Confusion Matrices are plotted for each model's performance on the Train set and the Test sets to highlight the respective strengths and weaknesses of each classifier.

**Logistic Regression (Tuned):**
![confusion-matrices-tuned-logistic-regression-model](https://github.com/user-attachments/assets/60876a95-4048-41fe-abd3-c39a1231c70e)

**Decision Tree (Tuned):**
![confusion_matrices-tuned-decision-tree-classifier](https://github.com/user-attachments/assets/915d82c1-03f0-429a-94bb-661a1e8153e6)

**Gradient Boosting (Tuned):**
![confusion-matrices-tuned-gradient-boosting-classifier](https://github.com/user-attachments/assets/14558041-5d16-4ce8-aa52-58fc52802b11)



### ROC Curves
ROC curves visualize each model's trade-off between sensitivity and specificity for each category of the target variable. The Area Under the Curve (AUC) highlights each classifier's discrimination ability.

**Logistic Regression (Tuned):**
![roc-curves-tuned-logistic-regression-model](https://github.com/user-attachments/assets/12cebc53-acaa-4120-a94b-e74c5c6edfd1)

**Decision Tree (Tuned):**
![roc-curves-tuned-decision-tree-classifier](https://github.com/user-attachments/assets/763ecf3f-b43f-427f-b373-5707f3bff1bf)

**Gradient Boosting (Tuned):**
![roc-curves-tuned-gradient-boosting-classifier](https://github.com/user-attachments/assets/cd5b1ca5-2fae-4455-89d3-f04e26591f82)


**Selected Model for Deployment:** -The Gradient Boosting Classifier consistently outperformed other models, achieving the highest accuracy and balanced performance across all classes, as evidenced by the evaluation metrics and visualizations.


### Top 15 Important Features

![top-15-important-features](https://github.com/user-attachments/assets/1914bcf7-b18e-43de-b817-f258566f0ddd)



## 6. Conclusion

The analysis demonstrates that tuned supervised ML models can effectively predict the condition of water wells using appropriately preprocessed features. The tuned Gradient Boosting Classifier is particularly a powerful, highly generalizable model that stakeholders in the Tanzanian water sector can leverage to to anticipate well failures and plan interventions proactively. This model was validated by predicting the class of a water-well's functional status for 14,850 entries from a previously unseen dataset (**testdata.csv**).

## 7. Business Recommendations

- **Prioritize Maintenance:** Model predictions can be used to identify wells at risk and allocate maintenance resources efficiently.
- **Data Collection:** Continued improvement of data quality, especially for key features influencing well condition, is recommended.
- **Stakeholder Engagement:** Insights should be shared with local authorities and NGOs to inform decision-making and maximize impact.

## 8. Next Steps

- **Model Deployment:** Integration of the best-performing model into a user-friendly dashboard for real-time predictions.
- **Feature Expansion:** Incorporation of additional data sources (e.g., weather, usage patterns) to enhance model accuracy.
- **Continuous Monitoring:** Regular updates to the model with new data to maintain performance and relevance.
