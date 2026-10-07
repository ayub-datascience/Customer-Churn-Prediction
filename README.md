# Customer Churn Prediction

## 📌 Project Overview

**Customer-Churn-Prediction** is a machine learning classification project designed to predict whether a customer is likely to **churn (leave the company's service or subscription)**.

The primary objective of this project is to identify as many potential churners as possible. Therefore, **Recall** is used as the primary evaluation and model-selection metric.

In a customer churn problem, missing a customer who is actually going to churn can be more costly than incorrectly identifying a customer as a potential churner. For this reason, the project prioritizes **minimizing False Negatives**.

---

## 🎯 Project Objective

The main objective is:

> **Identify as many customers likely to churn as possible while minimizing false negatives.**

The project follows an end-to-end machine learning workflow:

1. Define the problem
2. Understand and clean the dataset
3. Perform Exploratory Data Analysis (EDA)
4. Split the data into training and testing sets
5. Create preprocessing pipelines
6. Train multiple classification models
7. Evaluate the models
8. Perform 10-fold cross-validation
9. Select the best model based on Recall


## 🔄 Machine Learning Workflow

### 1. Defining the Problem

The problem is formulated as a **binary classification problem**.

The model predicts whether a customer will:

* `0` → Not Churn
* `1` → Churn

The focus is on detecting customers belonging to the **Churn = 1** class.

---

### 2. Understanding and Cleaning the Dataset

The dataset was inspected to understand:

* Dataset dimensions
* Feature types
* Missing values
* Duplicate records
* Numerical and categorical variables
* Target variable

Appropriate data-cleaning and preprocessing steps were applied before model training.

---

### 3. Exploratory Data Analysis

Exploratory Data Analysis was performed to understand patterns and relationships within the dataset.

The analysis included:

* Distribution of variables
* Churn distribution
* Relationships between features and churn
* Identification of potential patterns associated with customer churn

EDA helps understand the dataset before applying machine learning algorithms.

---

### 4. Train-Test Split

The dataset was divided into training and testing sets using **StratifiedShuffleSplit** from Scikit-learn.

Since **`Churn`** is the target variable, the split was performed using `Churn` as the stratification variable.

The purpose of stratification is to ensure that the distribution of the two target classes:

* `0` → Customer did not churn
* `1` → Customer churned

remains approximately consistent in both the training and testing datasets.

This is particularly important for a classification problem because an uneven distribution of the target classes between the training and testing sets could lead to unreliable model evaluation.

The splitting process follows these steps:

1. The original dataset is divided into training and testing sets.
2. `Churn` is used as the stratification variable.
3. `StratifiedShuffleSplit` randomly creates the split while preserving the class distribution.
4. The resulting training and testing datasets maintain approximately the same proportion of churn and non-churn customers as the original dataset.
   
---

### 5. Preprocessing Pipeline

A preprocessing pipeline was created to ensure that data transformations are applied consistently.

Depending on the feature type, preprocessing may include:

* Numerical feature transformation
* Categorical feature encoding

Using a pipeline also helps prevent **data leakage** during cross-validation.

---

## 🤖 Machine Learning Models

Four classification algorithms were trained and evaluated:

### 1. Logistic Regression

A linear classification algorithm used as a baseline model.

### 2. Decision Tree Classifier

A tree-based classification algorithm that makes predictions using a sequence of feature-based decision rules.

### 3. Random Forest Classifier

An ensemble model consisting of multiple decision trees whose predictions are combined to improve generalization.

### 4. Gradient Boosting Classifier

An ensemble learning algorithm that builds models sequentially, with each new model attempting to improve upon the errors of previous models.

---

## 📊 Model Evaluation

Since the primary objective is to identify as many customers likely to churn as possible, **Recall** was selected as the primary evaluation metric.

### Recall

Recall measures the proportion of actual churners that were correctly identified by the model.

```text
Recall = True Positives / (True Positives + False Negatives)
```

In this project:

* **True Positive (TP):** Customer actually churned and the model predicted churn.
* **False Negative (FN):** Customer actually churned but the model predicted no churn.

Therefore, a high Recall means the model is successful at finding customers who are actually going to churn.

### Why Recall?

Consider the following situation:

> A customer is actually going to leave the company's service, but the model predicts that the customer will stay.

This is a **False Negative**.

For a churn-prevention system, such a mistake can be costly because the company loses the opportunity to take preventive action.

Therefore, this project prioritizes **Recall over Accuracy**.

---

## 🔁 Cross-Validation

To obtain a more reliable estimate of model performance, **10-fold cross-validation** was used.

In 10-fold cross-validation:

1. The training dataset is divided into 10 folds.
2. Nine folds are used for training.
3. One fold is used for validation.
4. The process is repeated 10 times.
5. Each fold is used as the validation set once.
6. The Recall scores from all folds are returned.

The cross-validation scoring metric was:

```python
scoring="recall"
```

This allows the models to be compared based on their ability to correctly identify customers who churn.

---

## 🏆 Model Selection

Based on the 10-fold cross-validation results, the **Decision Tree Classifier** achieved the best performance for the project's primary objective.

### Best Model: Decision Tree Classifier

The Decision Tree Classifier achieved an average 10-fold cross-validation Recall of approximately:

```text
99.991%
```

It also demonstrated extremely consistent performance across the cross-validation folds.

### Why Decision Tree?

The Decision Tree was selected because:

* It achieved the **highest Recall Values** among the evaluated models.
* It demonstrated highly consistent performance across the 10 folds.
* It effectively identified customers belonging to the churn class.
* It aligns directly with the project's primary objective of minimizing false negatives.

Therefore:

> **Decision Tree Classifier was selected as the best-fit model because it achieved the highest cross-validation Recall, which is the primary model-selection criterion for this project.**


## 🧠 Business Interpretation

The model can be used to identify customers who are at high risk of churning.

A company could potentially use these predictions to:

* Identify high-risk customers
* Offer targeted discounts
* Provide personalized offers
* Improve customer support
* Contact dissatisfied customers
* Develop customer-retention strategies

The model should therefore be viewed as a **customer-retention decision-support tool**, rather than an automatic decision-making system.

---

## ⚠️ Important Consideration

Although Recall is the primary metric for this project, a very high Recall should not automatically be interpreted as perfect model performance.

A model can achieve extremely high Recall while potentially producing a large number of **False Positives**.

Therefore, before deploying the model in a real-world environment, additional metrics should also be considered, including:

* Precision
* F1-score
* Confusion Matrix
* ROC-AUC
* Precision-Recall Curve

The final business decision should balance the cost of:

* Missing a customer who will churn (**False Negative**)
* Incorrectly targeting a customer who would not have churned (**False Positive**)

---

## 🛠️ Technologies Used

* **Python**
* **Pandas** — Data manipulation
* **NumPy** — Numerical computation
* **Matplotlib** — Data visualization
* **Seaborn** — Statistical visualization
* **Scikit-learn** — Machine learning and model evaluation
* **Jupyter Notebook** — Development and experimentation

---

## 📚 Key Machine Learning Concepts Demonstrated

This project demonstrates practical understanding of:

* Binary Classification
* Data Cleaning
* Exploratory Data Analysis
* Train-Test Split
* Feature Preprocessing
* Machine Learning Pipelines
* Logistic Regression
* Decision Trees
* Random Forest
* Gradient Boosting
* Cross-Validation
* Recall
* Model Comparison
* Model Selection
* Customer Churn Prediction

---

## 🚀 Future Improvements

Possible improvements to the project include:

* Hyperparameter tuning using `GridSearchCV` or `RandomizedSearchCV`
* Handling class imbalance using appropriate techniques
* Threshold optimization
* Precision-Recall curve analysis
* Feature importance analysis
* SHAP-based model explainability
* Cost-sensitive learning
* Testing additional ensemble algorithms
* Deploying the final model using Streamlit or Flask/FastAPI
* Creating a customer churn prediction API
* Developing a dashboard for monitoring high-risk customers

---

## 📌 Conclusion

This project demonstrates an end-to-end approach to solving a **customer churn prediction problem using machine learning**.

Four classification models were trained and compared:

* Logistic Regression
* Decision Tree Classifier
* Random Forest Classifier
* Gradient Boosting Classifier

Because the primary objective is to identify as many customers likely to churn as possible, **Recall was selected as the primary cross-validation scoring metric**.

Based on the 10-fold cross-validation results, the **Decision Tree Classifier** achieved the highest mean Recall of approximately **99.991%** and demonstrated highly consistent performance across the folds.

Therefore, the **Decision Tree Classifier was selected as the best-fit model for this project's stated objective**.

---

## 👨‍💻 Author

**Ayub**

Engineering Student | Aspiring Data Scientist / Machine Learning Intern

---
