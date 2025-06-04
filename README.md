# Supervised ML Classifiers for Predicting Water Wells Condition

## 1. Project Overview

This project explores the use of supervised machine learning classifiers to predict the condition of water wells in Tanzania. By leveraging a ternary classification approach, the goal is to distinguish between wells that are functional, non-functional, or functional but in need of repair. The workflow encompasses data preprocessing, model building, evaluation, and actionable recommendations to support sustainable water resource management.

## 2. Business Understanding

Access to clean and reliable water is a critical challenge in Tanzania. Many wells fall into disrepair or become non-functional, impacting communities' health and livelihoods. Predicting the condition of water wells enables stakeholders to prioritize maintenance, allocate resources efficiently, and ensure long-term water access. This project addresses the question: **Can the operational status of water wells be accurately predicted using available data and machine learning?**

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

### Performance Metrics
The respective performance of the three classifiers is quantified based on **F1-score**, and **ROC-AUC**.

| Model                     | Train F1-score | Test F1-score | Train ROC-AUC | Test ROC-AUC |
|---------------------------|----------------|---------------|---------------|--------------|
| Logistic Regression (Untuned) | 0.650390       | 0.674233      | 0.831460      | 0.816319     |
| Logistic Regression (Tuned)   | 0.650930       | 0.671800      | 0.832009      | 0.816467     |
| Decision Tree (Untuned)   | 0.999461       | 0.657666      | 1.000000      | 0.731613     |
| Decision Tree (Tuned)     | 0.812901       | 0.667340      | 0.953505      | 0.801969     |
| Gradient Boosting (Untuned) | 0.721155       | 0.698047      | 0.879053      | 0.843328     |
| Gradient Boosting (Tuned)   | 0.817773       | 0.710658      | 0.944834      | 0.863916     |


**Selected Model for Deployment:** -The Hyperparameter-tuned Gradient Boosting Classifier consistently outperformed other models, achieving the highest F1-score, ROC-AUC. These metrics justify the classifier's balanced performance across all classes. The superiority of the Ensemble ML model is also justified by the relatively larger number of True Positives, and True Negatives as captured in its confusion matrices (train and test) compared to the other classifiers.


### Top 15 Important Features

![top-15-important-features](https://github.com/user-attachments/assets/1914bcf7-b18e-43de-b817-f258566f0ddd)



## 6. Conclusion

The analysis demonstrates that tuned supervised ML models can effectively predict the condition of water wells using appropriately preprocessed features. The tuned Gradient Boosting Classifier is particularly a powerful, highly generalizable model that stakeholders in the Tanzanian water sector can leverage to to anticipate well failures and plan interventions proactively. This model was validated by predicting the class of a water-well's functional status for 14,850 entries from a previously unseen dataset (**testdata.csv**).

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


