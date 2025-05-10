# Recommending Mobile Plans: A Machine Learning Approach for Megaline

## Project Overview

This project builds a machine learning model to help **Megaline**, a mobile carrier, recommend customers the most suitable mobile plan — **Smart** or **Ultra** — based on their monthly usage patterns. The classification model leverages user behavior data such as number of calls, messages, call duration, and data usage to personalize plan suggestions.

## Project Objectives

The main objectives of this project are:
1. Analyze subscriber behavior using historical usage data.
2. Build and compare classification models to predict plan preference.
3. Tune hyperparameters for optimal model performance.
4. Evaluate model accuracy on unseen data and validate it against baseline strategies.

## Features

### 1. Data Preparation
- Load and inspect the dataset (`users_behavior.csv`).
- Handle missing values and confirm data types.
- Check for and handle duplicates.
- Analyze correlations between features to inform modeling decisions.

### 2. Modeling and Validation
- Train multiple models:
  - **Logistic Regression**
  - **Decision Tree**
  - **Random Forest**
- Perform hyperparameter tuning on decision trees and forests.
- Evaluate models using accuracy on a validation set.

### 3. Final Evaluation
- Combine training and validation sets to train the final model.
- Assess model performance on a separate, untouched test set.
- Run sanity checks using:
  - Random predictions
  - Most frequent class baseline

## Technologies Used

- **Python**: Main programming language  
- **Pandas**: Data analysis and manipulation  
- **NumPy**: Numerical operations  
- **scikit-learn**: Machine learning models and metrics  
- **Jupyter Notebook**: Analysis environment

## Dataset

- `users_behavior.csv`: Contains monthly data on subscriber behavior:
  - `calls`: Number of calls
  - `minutes`: Total minutes of calls
  - `messages`: Number of text messages
  - `mb_used`: Internet traffic used (MB)
  - `is_ultra`: Target variable (1 = Ultra, 0 = Smart)

## Analysis Workflow

### 1. Data Loading & Inspection
- Preview structure and summary statistics
- Analyze correlation matrix (notably, calls and minutes show strong correlation)

### 2. Model Training & Tuning
- Evaluate model performance on validation set.
- Tune `max_depth` for Decision Tree and both `n_estimators` and `max_depth` for Random Forest.

### 3. Final Model Testing
- Train the best model on full training+validation set.
- Test on unseen data and compare against baselines.

## Key Findings

1. The **Random Forest** model with `n_estimators=20` and `max_depth=15` achieved the best results:
   - **Validation accuracy**: 80.2%
   - **Test accuracy**: 78.4%
2. The model outperformed both:
   - **Random guess baseline**: ~50%
   - **Most frequent class** baseline: ~69.5%
3. High correlation between `calls` and `minutes` was retained, as Random Forests handle multicollinearity well.

## Project Structure

- `mobile_plan_classification.ipynb`: Main notebook with full analysis and modeling.
- `data/`
    - `users_behavior.csv`
- `README.md`: Project summary and insights.