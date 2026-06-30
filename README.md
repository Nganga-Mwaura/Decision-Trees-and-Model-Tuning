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
### Model Performance Comparison

Model	Training :Recall	,CV Recall	,Test Recall	,Overfitting Gap

Baseline	1.000	,0.871 ,0.860	,0.129

Random Search	0.926	,0.907	,0.900	,0.019

Grid Search (Final)	0.921	,0.901	,0.901
