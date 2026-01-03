# DS230 Final Project – Instacart Reorder Prediction

## Project Overview
This project analyzes the Instacart Market Basket Analysis dataset to predict whether a product will be reordered by a user in their next order.  
The project follows a complete machine learning workflow including exploratory data analysis, feature engineering, handling class imbalance, and classification modeling.

## Dataset
Instacart Market Basket Analysis dataset (Kaggle), composed of multiple relational tables:
- orders
- order_products (prior/train)
- products
- aisles
- departments

All data ingestion, joins, and preprocessing steps were performed programmatically in Python.

## Exploratory Data Analysis (EDA)
- Missing value analysis
- Distribution analysis for numerical features
- Target variable (`reordered`) distribution
- Categorical analysis for aisles and departments
- Correlation analysis between numerical features
- Temporal analysis:
  - Orders by hour of day
  - Orders by day of week
  - Weekday vs weekend behavior

## Data Cleaning & Preprocessing
- Missing values were inspected and documented
- Outliers were examined using boxplots
- Non-numeric columns were excluded from modeling
- Feature scaling was applied to numerical features using MinMax scaling

## Feature Engineering
The following features were constructed:

### User-level Features
- Total number of orders
- Average basket size
- Mean days between orders
- Reorder ratio

### Product-level Features
- Product reorder rate
- Average cart position
- Product popularity statistics

### User-Product Interaction Features
- Prior purchase count
- User-product recency
- Average reorder probability

### Temporal Features
- Order hour of day
- Order day of week
- Weekend indicator

## Dimensionality & Collinearity
- Feature correlation analysis was conducted
- Highly correlated features (|ρ| ≥ 0.95) were removed
- Variance Inflation Factor (VIF) was used to assess multicollinearity
- Feature reduction was applied to improve model stability

## Classification Task
**Task:** Predict whether a product will be reordered (`reordered`).

### Models Implemented
- Logistic Regression (baseline)
- Logistic Regression with class weights

## Imbalanced Data Handling
- The target variable was imbalanced
- Class weights were applied to reduce bias toward the majority class
- Performance was compared before and after imbalance correction

## Time-aware Data Splitting
To avoid data leakage, the dataset was split based on the chronological order of the data rather than random sampling.  
This design choice was documented directly in the code using explanatory comments to ensure temporal consistency.

## Evaluation Metrics
Models were evaluated using:
- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC

## Project Files
- `Project.ipynb`: Full pipeline including EDA, preprocessing, feature engineering, and modeling
- `data/`: Dataset files
- `README.md`: Project documentation

## Work Contribution & Understanding Statement

- **Ghena Omar Hussien:**
  - Understanding of the submitted work: approximately 99%.

- **Oraib Metib bni Khaled:**
  - Understanding of the submitted work: approximately 40%.

The submitted work represents approximately 50% (Preprocessing)of the overall project requirements.



## Notes
Due to focusing on `eval_set = 'train'` during preprocessing, the constructed dataset contains only one order per user, which makes a time-aware split infeasible.  
Therefore, evaluation relies on a stratified random split, as documented directly in the code.

