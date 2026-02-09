Restaurant Aggregate Rating Prediction

Project Overview

This project applies machine-learning regression techniques to predict restaurants' aggregate ratings using historical restaurant data. 
Aggregate ratings reflect customer satisfaction and are critical for restaurant recommendation systems, customer decision-making, and restaurant owner performance evaluation.
The notebook walks through the complete data science pipeline, from data exploration and cleaning to model training, evaluation, and comparison.

Problem Statement

Given a dataset containing restaurant attributes, the goal is to build a predictive model that can accurately estimate a restaurant’s aggregate rating.
This is formulated as a supervised regression problem.

Dataset Description

The dataset contains multiple features describing restaurants, including operational and rating-related attributes.

Target Variable:
Aggregate rating (continuous numerical variable)

Feature Types:
Numerical features
Categorical features (encoded during preprocessing)

Project Workflow

Library Import

The project uses standard Python data science libraries: pandas, numpy for data manipulation, matplotlib, seaborn for visualization, scikit-learn for modeling and evaluation

Data Loading and Inspection

Dataset is loaded into a Pandas DataFrame

Initial inspection includes:

Shape of the dataset

Column names and data types

Missing values and inconsistencies

Exploratory Data Analysis (Initial)
 
Summary statistics for numerical variables

Distribution of the aggregate rating

Identification of skewness, outliers, and data quality issues

Initial understanding of feature relevance

Data Cleaning and Wrangling

This step ensures the dataset is suitable for machine learning:

Handling missing values

Dropping irrelevant or redundant columns

Encoding categorical variables

Exploratory Data Analysis (Post-Cleaning)

Validation of cleaning steps

Reassessment of distributions and feature relationships

Visual confirmation of improved data quality

Train–Test Split: The dataset is split into training and testing sets
   
Modeling Approach

Three regression models were trained and evaluated:

Linear Regression

Decision Tree Regressor

Random Forest Regressor

Model Evaluation

Models were evaluated using standard regression metrics:

R² Score: measures how well the model explains variance in ratings

Mean Squared Error (MSE) / Root Mean Squared Error (RMSE): measures prediction error

Performance comparison shows that ensemble models outperform simpler models, with Random Forest achieving the best results.

Key Insights

Data preprocessing significantly improved model performance. 

Non-linear models performed better than linear regression

Random Forest provided the most accurate predictions

Feature selection and cleaning were critical to reducing error
