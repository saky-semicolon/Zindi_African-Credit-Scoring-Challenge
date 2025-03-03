# African Credit Scoring Challenge

## Project Overview
This repository contains the implementation for the **African Credit Scoring Challenge** hosted on [Zindi](https://zindi.africa/competitions/african-credit-scoring-challenge). The challenge involved predicting the likelihood of a customer defaulting on a loan based on financial data. The project utilizes **deep learning techniques** combined with **feature engineering** and **hyperparameter optimization** to achieve high predictive performance.

## Dataset
The dataset consists of:
- **Training Data**: Customer financial records with features like loan type, demographics, and repayment history.
- **Test Data**: Customer records without target labels, used for final evaluation.
- **Target Variable**: A binary classification label indicating **loan default (1) or no default (0).**

## Key Features & Methodology
### 1. Data Preprocessing
- **Handling Missing Values:**
  - Numerical features were imputed with the mean.
  - Categorical features were imputed with the mode.
- **Feature Engineering:**
  - `days_to_repay`: Difference between loan disbursement date and due date.
  - `repay_ratio`: Ratio of total repayment amount to original loan amount.
  - `amount_duration_ratio`: Ratio of loan amount to loan duration.
  - `disbursement_month`: Extracted from the disbursement date.
  - Interaction terms such as `amount_duration_interaction` and `repay_duration_interaction`.
- **Categorical Encoding:**
  - Label encoding for categorical variables such as `loan_type` and `country_id`.
- **Normalization:**
  - Standardization using `StandardScaler` to ensure zero mean and unit variance.
- **Class Balancing:**
  - **ADASYN (Adaptive Synthetic Sampling)** was used to balance class distribution.
- **Data Splitting:**
  - 80-20 split into training and validation sets.

### 2. Deep Learning Model
The architecture is based on a **Wide and Deep Learning** framework:
- **Wide Layer**: Captures simple feature interactions.
- **Deep Layers**:
  - **LayerNorm** for stable training.
  - **LeakyReLU** activation.
  - **Dropout** for regularization.
- **Output Layer**:
  - Single neuron with **sigmoid activation** for binary classification.
- **Final Prediction**:
  - Combines outputs from wide and deep layers.

### 3. Hyperparameter Optimization
Used **Optuna** for automated tuning of:
- Hidden layer size (64-256 neurons).
- Dropout rate (0.2-0.5).
- Learning rate (1e-5 to 1e-2).
- Batch size (32, 64, 128).

### 4. Training Strategy
- **Loss Function**: Binary Cross-Entropy Loss (BCELoss).
- **Optimizer**: AdamW with weight decay.
- **Learning Rate Scheduler**: OneCycleLR for dynamic adjustments.
- **Early Stopping**: Best model saved based on validation F1 score.

## Model Performance & Leaderboard Progression
| Date | Experiment | Public Score | Private Score |
|------|-----------|--------------|--------------|
| Dec 29, 2024 | Baseline Model | 0.60 | 0.59 |
| Jan 2, 2025 | Feature Engineering | 0.62 | 0.59 |
| Jan 5, 2025 | ADASYN Class Balancing | 0.66 | 0.63 |
| Jan 8, 2025 | Wide and Deep Model | 0.67 | 0.64 |
| Jan 10, 2025 | Optuna Hyperparameter Tuning | 0.67 | 0.65 |
| Jan 12, 2025 | Final Submission (Ensemble) | 0.69 | 0.65 |

Final ranking: **381st place** with a public score of **0.6977** and private score of **0.6543**.

## Future Work
- **Exploring Transformer-based models** for tabular data.
- **Incorporating external datasets** (e.g., macroeconomic indicators).
- **Applying SHAP/LIME** for model interpretability.
- **Ensembling different architectures** for better generalization.

## Installation & Usage
### Clone the Repository
```bash
git clone https://github.com/yourusername/african-credit-scoring.git
cd african-credit-scoring
```

