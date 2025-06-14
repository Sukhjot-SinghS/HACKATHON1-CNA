# HACKATHON1-CNA
🌱 NDVI Land Cover Classification – Summer Analytics Hackathon 2025
🚀 Overview
This repository contains my end-to-end solution for the Summer Analytics Mid Hackathon 2025, where the goal was to classify land cover types using multi-temporal NDVI (Normalized Difference Vegetation Index) satellite data. The challenge was made more interesting by the constraint: only multiclass logistic regression models were allowed.

🗂️ Problem Statement
Given time-series NDVI data for thousands of locations, predict the correct land cover class (e.g., forest, farm, grass, water, orchard, impervious) for each test sample. The dataset is highly imbalanced, with some classes (like orchard and water) being extremely rare.

🛠️ Approach
1. Data Cleaning
NDVI Rescaling: Converted raw NDVI values to the [-1, 1] range.

Outlier Handling: Capped NDVI values to plausible vegetation ranges ([-0.2, 0.9]).

Missing Value Imputation: Used a combination of median neighbor filling and linear interpolation to address missing or abnormal values.

2. Feature Engineering
Seasonal Features: Computed mean, standard deviation, max, min, and amplitude for each season (Winter, Spring, Summer, Fall) and for each year.

Trend Features: Calculated NDVI slope (trend), peak, trough, and overall amplitude for each sample.

Polynomial Features: Added interaction and squared terms to help logistic regression capture non-linear relationships.

(Advanced versions): Included monthly stats, NDVI differences between time points, and NDVI entropy as texture features.

3. Modeling
Multiclass Logistic Regression: Used multinomial logistic regression with class_weight='balanced' to address class imbalance.

Pipeline: Combined scaling, feature selection (L1-based), and polynomial feature expansion in a single scikit-learn pipeline.

Hyperparameter Tuning: Grid-searched over regularization strength (C) and iteration limits (max_iter) using stratified cross-validation.

4. Submission
Generated predictions for the test set and formatted them for Kaggle submission as submission_results.csv.

📊 Results
Metric	Score
Public Leaderboard	0.70
Private Leaderboard	0.63
Baseline (raw NDVI + logistic regression): ~0.37

💡 Key Learnings
Feature engineering is king: Extracting seasonal, trend, and interaction features from NDVI time series is essential for strong performance with linear models.

Class imbalance is tough: Even with class weighting, rare classes remain challenging for logistic regression.

Model limitations: Logistic regression is robust and interpretable, but cannot capture all the complexity in multi-temporal satellite data. Higher accuracy would require tree-based or deep learning models, which were not allowed here.

Reproducibility: The pipeline is fully reproducible and ready for extension or adaptation.
👤 Author
Sukhjot Singh

📝 Acknowledgments
Thanks to the Summer Analytics Hackathon organizers and the Kaggle community.
