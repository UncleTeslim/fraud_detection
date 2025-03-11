# Credit Card Fraud Detection

## Project Overview
This project focuses on detecting fraudulent credit card transactions using machine learning techniques. The dataset contains a highly imbalanced distribution of fraud and non-fraud transactions, requiring careful handling of class imbalance. Various models were trained, including Random Forest, and XGBoost as base models, and ensemble techniques such as Voting and Stacking Classifiers. For the ensemble technique, I used Random Forest and XGBoost as Base Learners and Logistic Regression as the Meta-learner.

## Dataset
- The dataset contains transaction details with features extracted from real-world financial data.
- The target variable (`is_fraud`) has two values:
  - `0`: Legitimate transactions
  - `1`: Fraudulent transactions
- The dataset is highly imbalanced, requiring resampling techniques to improve detection performance.

## Data Preprocessing
### 1. Handling Class Imbalance
- Applied **Random Undersampling (x3)** to balance the dataset.

### 2. Feature Engineering
- Scaled numerical features for better model convergence.
- Ensured no data leakage between training and test sets.

### 3. Train-Test Split
- 80% training, 20% testing.
- Stratified splitting to maintain class distribution.

## Models and Performance
The following models were trained and evaluated:

### 1. Random Forest (Best Performing Individual Model)
- **AUC-ROC Score:** `0.9144`
- **F1-Score for Fraud:** `0.86`
- **Recall for Fraud:** `0.89`
- **Precision for Fraud:** `0.83`
- **Observation:** Strong precision and recall, robust against class imbalance.

### 2. XGBoost (Best Individual Model for AUC-ROC)
- **AUC-ROC Score:** `0.9793`
- **F1-Score for Fraud:** `0.87`
- **Recall for Fraud:** `0.83`
- **Precision for Fraud:** `0.91`
- **Observation:** Slightly better than Random Forest, but higher false negatives.

### 3. Voting Classifier (Random Forest + XGBoost)
- **AUC-ROC Score:** `0.9007`
- **F1-Score for Fraud:** `0.87`
- **Recall for Fraud:** `0.83`
- **Precision for Fraud:** `0.90`
- **Observation:** Performed well, but stacking improved results.

### 4. Stacking Classifier (Final Model: Random Forest + XGBoost + Logistic Regression)
- **AUC-ROC Score:** `0.9162`
- **F1-Score for Fraud:** `0.86`
- **Recall for Fraud:** `0.89`
- **Precision for Fraud:** `0.83`
- **Observation:** Best recall for fraud cases, reducing false negatives significantly.

## Key Takeaways
- **Stacking Classifier was the best-performing model**, achieving the highest recall for fraud cases while maintaining strong overall accuracy.
- **Random Forest and XGBoost individually performed well**, but their combination in stacking improved results.
- **Handling class imbalance effectively** (via undersampling) was crucial in improving fraud detection.

## Deployment Considerations
- The final model can be deployed via **Flask** or **FastAPI**.
- Integration with **financial transaction systems** for real-time fraud detection.
- Continuous model retraining with updated transaction data.

## Future Improvements
- Experiment with deep learning models (LSTMs for sequential transaction patterns).

How to Run the Project

1. Clone the Repository
``` bash
git clone https://github.com/your-repo/fraud-detection.git
cd fraud-detection
```
2. Install Dependencies
```bash
pip install -r requirements.txt
```
