# Machine Learning with Python - Summary

## Author: Pablo Nunes

----

## Introduction

- Definition: Machine Learning is the subfield of computer science that gives "computers the ability to learn without being explicitly programmed" (Arthur Samuel)
- How ML works?
  - Data -> Feature Extraction -> Rule Set -> Results
- Major ML techniques
  - Regression/Estimation - Predicting continuous values
  - Classification - Predicting the item class/category of a case
  - Clustering - Finding the structure of data
  - Associations - Associating frequent co-occurring events
  - Anomaly detection - Discovering abnormal and unusual cases
  - Sequence mining - Predicting next events
  - Dimension Reduction - Reducing the size of data
  - Recommendation systems - Recommending items
- AI vs. Machine Learning vs. Deep Learning
- Python libraries for ML
  - Numpy - Efficient computations
  - SciPy - Toolbox
  - MatPlotLib - Plot
  - Pandas - Data Structures
  - SciKit Learn - ML
- SciKit Learn
  - Free software
  - Classification, Regression and Clustering algorithms
  - Works with NumPy and SciPy
  - Great Documentation
  - Easy to implement
- Supervised vs Unsupervised
  - Supervised: Labeled data
  - Unsupervised: Unlabeled data

## Regression

- What is regression: Process of predicting a continuous value
- We have the independent variables and the dependent variable, trying predict the dependent one.
- Types of regression
  - Simple Linear Regression
  - Simple Non-Linear Regression
  - Multiple Linear Regression
  - Multiple Non-Linear Regression
- Applications of regression
  - Forecasting
  - Analysis
  - Price Estimation
- Regression algorithms
  - Ordinal Regression
  - Poisson Regression
  - Fast forest regression
  - Linear, Polynomial, Lasso, Stepwise, Ridge Regression
  - Bayesian Linear Regression
  - Neural Network regression
  - Decision Forest Regression
  - KNN
- Simple Linear Regression
  - This regression uses only one independent variable to predict a dependent variable
  - Using a linear function, y = theta_0 + theta_1 * x_1
  - So, we need to find theta_0 and theta_1
  - Using the Medium Squared Error, we have to minimize it using theta_0 and theta_1.
- Model Evaluation
  - Train and Test on the Same Dataset VS. Train/Test Split
  - To calculate the error, just compare the predicted vs reality, and average them.
  - Training Accuracy vs. Out-of-sample accuracy
  - K-fold cross validation
