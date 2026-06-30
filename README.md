# Customer Churn Prediction Using Decision Trees
A machine learning project that predicts customer churn for a telecommunications company, enabling proactive retention strategies and reducing revenue loss.

## Objective
Problem: Telecom companies lose significant revenue when customers cancel their service (churn), and identifying at-risk customers early is challenging with manual methods.

Goal: Build a decision tree model that accurately predicts which customers are likely to churn, allowing the company to proactively reach out with retention offers and save valuable customers.

## Dataset
Source: Telecom customer churn dataset (synthetic/processed data)

Rows: 20,000 customer records

Features: 13 customer attributes

Target: churn (0 = No Churn, 1 = Churn)

## Features Description:
Feature	Description

account_age_months - How long the customer has been with the company

monthly_charges	- Monthly bill amount

subscription_tier	- Tier level of subscription (1, 2, 3)

support_calls	- Number of customer support calls

reported_issues	- Number of issues reported

inactive_days	- Days with no account activity

usage_decline	- Percentage decrease in service usage

competitor_offer - Whether customer received a competitor offer

promotion_response	- Response to past promotions

contract_type	- Type of contract (month-to-month, yearly, etc.)

payment_method	- Method of payment

online_security	- Whether customer has online security add-on

tech_support	- Whether customer has tech support add-on

## Tools & Technologies
Python 3.8+

Pandas - Data manipulation

NumPy - Numerical operations

Scikit-learn - Machine learning (Decision Trees, Cross-validation, Hyperparameter Tuning)

Matplotlib - Data visualization

Seaborn - Advanced visualization

Jupyter Notebook - Development environment

## Workflow
### 1. Data Loading & Exploration
Loaded dataset and examined structure

Checked for missing values and data types

Analyzed target distribution (churn rate)

### 2. Data Preparation
Separated features (X) and target (y)

Split data into training (75%) and testing (25%) sets with stratification

Used random_state=42 for reproducibility

### 3. Baseline Model Development
Created an untuned Decision Tree classifier

Evaluated with 5-fold cross-validation

Identified overfitting issues (training recall = 1.000, CV recall = 0.871)

### 4. Hyperparameter Tuning
Randomized Search (Broad Exploration):

Tested 50 random combinations across wide ranges

Explored parameters: criterion, max_depth, min_samples_split, min_samples_leaf

Found promising region: depth ~89, split ~4, leaf ~13

Grid Search (Focused Refinement):

Narrowed parameter ranges based on random search results

Tested 100 specific combinations

Found optimal parameters with 3-fold cross-validation

### 5. Final Model Evaluation
Evaluated best model on held-out test set

Generated confusion matrix

Calculated business impact metrics

Analyzed feature importance

### 6. Business Insights & Recommendations
Identified top churn predictors

Translated model findings into actionable business strategies

Provided recommendations for customer retention

## Results
### Best Parameters Found:
criterion = log_loss
max_depth = 85
min_samples_leaf = 15
min_samples_split = 3

### Model Performance Comparison:

Baseline Model - Training Recall: 1.000, CV Recall: 0.871, Test Recall: 0.860, Overfitting Gap: 0.129

Random Search - Training Recall: 0.926, CV Recall: 0.907, Test Recall: 0.900, Overfitting Gap: 0.019

Grid Search (Final) - Training Recall: 0.921, CV Recall: 0.901, Test Recall: 0.901, Overfitting Gap: 0.020

### Confusion Matrix (Final Model - Test Set):

True Negatives: 3,133 (loyal customers correctly identified)
False Positives: 154 (loyal customers incorrectly flagged)
False Negatives: 170 (churners missed by model - HIGH COST)
True Positives: 1,314 (churners correctly identified)

### Key Performance Metrics:

Recall (Primary Metric): 88.5%
Precision: 89.5%
Accuracy: 93.2%
F1-Score: 89.0%

## Business Impact:

85% reduction in overfitting from baseline

88.5% of churners correctly identified

30 more customers saved per 1,000 at-risk compared to baseline

## Key Insights
### Top 5 Churn Predictors:

monthly_charges (23.5%) - Customers with high bills are most likely to churn

subscription_tier (21.2%) - Lower tier customers are less committed

usage_decline (16.8%) - Declining usage indicates disengagement

support_calls (14.5%) - High support calls signal dissatisfaction

competitor_offer (8.8%) - Customers actively shopping for alternatives

## Business Recommendations:

Offer discounts or value-adds to high-charge customers to improve perceived value

Incentivize lower-tier customers to upgrade for better value and commitment

Re-engage customers showing usage decline with targeted campaigns

Proactively resolve issues for customers with high support calls

Match competitor offers with retention deals for at-risk customers

## Future Improvements
Implement ensemble methods like Random Forest and XGBoost for potential performance gains

Deploy model as real-time API for instant churn predictions

Add model monitoring dashboard to track recall in production

Use Bayesian optimization (Optuna) for more efficient hyperparameter tuning

Create interaction features between top predictors (e.g., monthly_charges × subscription_tier)
