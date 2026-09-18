# Credit Card Fraud Detection Using SMOTE

## Dataset

Dataset used in this project:  
[Kaggle - Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)

The dataset contains **284,807 credit card transactions**, with **492 fraudulent transactions**, making it a highly imbalanced classification problem. The dataset contains `Time`, `Amount`, `V1`–`V28`, and `Class`. The `V1`–`V28` features are anonymized PCA-transformed features. [Kaggle dataset](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)

## Class Imbalance

The target variable is `Class`:

- `0` → Legitimate/normal transaction
- `1` → Fraudulent transaction

The original dataset contains approximately:

- Class 0: **284,315** legitimate transactions
- Class 1: **492** fraudulent transactions

Because the classes are highly imbalanced, accuracy alone is not sufficient for evaluating the model.

## Handling Class Imbalance Using SMOTE

To handle the class imbalance, I used **SMOTE (Synthetic Minority Over-sampling Technique)**.

First, the data was divided into training and testing sets using a stratified split. SMOTE was then applied **only to the training data** to generate synthetic examples of the minority class (fraud).

This resulted in a more balanced training dataset without modifying the original test set.

## Models Used

Three classification models were trained:

1. **M1 – Logistic Regression**
2. **M2 – Random Forest**
3. **M3 – XGBoost**

The models were evaluated using Accuracy, Precision, Recall, F1-Score, and ROC-AUC.

## Evaluation Metrics

### Accuracy
Measures the percentage of all transactions that were classified correctly.

### Precision
Among all transactions predicted as fraud, precision tells us how many were actually fraudulent.

### Recall
Among all actual fraudulent transactions, recall tells us how many were successfully detected.

### F1-Score
The harmonic mean of precision and recall, providing a balance between the two.

### ROC-AUC
Measures how well the model distinguishes between legitimate and fraudulent transactions across different classification thresholds.

## Model Performance

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 93.91% | 97.78% | 89.80% | 93.62% | 97.53% |
| Random Forest | 92.89% | 98.84% | 86.73% | 92.39% | 97.22% |
| XGBoost | 92.89% | 97.73% | 87.76% | 92.47% | 97.29% |

## Results

On the given test split, **Logistic Regression achieved the highest accuracy, recall, F1-score, and ROC-AUC**, while **Random Forest achieved the highest precision**.

The three models showed similar overall performance, with ROC-AUC values above 0.97 on this test split.
