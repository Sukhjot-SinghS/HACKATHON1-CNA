# HACKATHON1-CNA
NDVI Land Cover Classification – Summer Analytics Hackathon 2025
🚩 Project Overview
This repository contains my solution for the Summer Analytics Mid Hackathon 2025. The task was to classify land cover types using time-series NDVI satellite data, with a focus on robust feature engineering and only multiclass logistic regression models, as required by the competition rules.

🌱 Problem Statement
Given multi-temporal NDVI data for various locations, the challenge is to accurately predict the land cover class (e.g., forest, farm, grass, water, orchard, impervious) for each test sample. The dataset is highly imbalanced, with some classes (like orchard and water) being rare.

🛠️ Solution Approach
Data Cleaning:

Rescaled NDVI values to [-1, 1]

Interpolated missing values and smoothed outliers

Capped NDVI values to plausible vegetation ranges

Feature Engineering:

Computed fine-grained monthly and seasonal statistics (mean, std, max, min, amplitude)

Calculated temporal trends (NDVI slope, peak, trough, amplitude)

Added polynomial and interaction features to capture non-linear relationships

Included temporal difference and phenological integral features

Modeling:

Used multinomial logistic regression with class weighting to handle imbalance

Applied feature scaling and L1-based feature selection

Hyperparameter tuning via GridSearchCV with stratified folds

Submission:

Generated predictions for the test set and formatted them for Kaggle submission

📈 Results
Public Leaderboard Score: 0.84 (as of latest submission)

Significant improvement over baseline logistic regression (0.37) due to advanced feature engineering
