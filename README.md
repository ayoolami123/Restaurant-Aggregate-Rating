🍽️ PREDICTING RESTAURANT AGGREGATE RATINGS

What makes a restaurant highly rated? Is it the price? The number of votes? The location? Or something deeper hidden in the data?

This project applies supervised machine learning to uncover the key drivers. 

📌 Project Overview

The goal of this project is to predict a restaurant’s aggregate rating using structured features such as location, pricing, votes, cuisines, and service options.

Rather than relying on intuition, we use exploratory data analysis (EDA), feature engineering, and multiple regression models to uncover what truly drives restaurant ratings.

📊 Dataset Summary

•	Initial dataset: 9,551 rows × 21 columns

•	After cleaning: 7,394 rows × 13 columns

•	Target variable: Aggregate rating

Feature types:

•	Categorical features (e.g., City, Country Code, Services)

•	Numerical features (e.g., Votes, Average Cost for Two, Price Range)

•	Geographic features (Latitude, Longitude)

🔎 Step 1: Exploratory Data Analysis (EDA)

We began by understanding the structure and quality of the dataset:

✅ No duplicate rows

⚠️ 9 missing values in Cuisines (removed during cleaning)

🚨 High-cardinality columns identified (Restaurant ID, Name, Address)

Key Insights from EDA

•	Most restaurant ratings fall between 3.0 and 3.8

•	A spike at 0.0 corresponds to Not Rated restaurants

•	Ratings are approximately bell-shaped after cleaning

•	Higher Votes → more stable and generally higher ratings

•	Higher Price Range → moderately higher ratings

•	Geographic patterns show India dominates the dataset

Correlation analysis revealed moderate relationships between:

•	Aggregate Rating and Votes

•	Aggregate Rating and Price Range

•	Aggregate Rating and Country Code

Interestingly:

Online delivery, Is delivering now and table booking had minimal influence on ratings.

🧹 Step 2: Data Wrangling & Feature Engineering

To improve model performance and reduce noise:

Removed:

•	High-cardinality identifiers (Restaurant ID, Name, Address)

•	Leakage features (Rating text, Rating color)

•	Redundant and multicollinearity-prone features (Switch-to-order menu, Locality Verbose, Currency)

Feature Engineering:

•	Frequency Encoding for City and Locality

•	Split and extracted Top 20 Cuisines

•	Label encoding for binary categorical variables

•	One-hot encoding for Country Code

After preprocessing, the dataset was model-ready.

🧠 Step 3: Modeling Strategy

•	Data Splitting: 80% Training, 20% Testing

•	Additional validation split for tree-based tuning

Baseline Model:

Used mean prediction to establish a benchmark (MAE).

🤖 Models Implemented

1️⃣ Linear Regression

•	Standardized inputs

•	Captures linear relationships

•	Serves as a simple interpretable benchmark

2️⃣ Decision Tree Regressor

•	Captures nonlinear relationships

•	Initially overfit

•	Hyperparameter tuning performed on max_depth

📈 Validation curve showed optimal performance at: max_depth = 4

Tuning significantly improved generalization.

3️⃣ Random Forest Regressor (Best Model 🏆)

•	Reduces variance

•	Captures complex nonlinear interactions

📊 Performance:

R² ≈ 0.62

Lowest RMSE among all models

This model outperformed both Linear Regression and Decision Tree.

🔍 Feature Importance Insights

Top predictive features included:

⭐ Votes	0.4669

⭐ City-Freq 	0.1388

⭐ Longitude	0.0807

⭐ Latitude	0.0698

⭐ Average Cost for Two	0.0528

📈 Interpretation

1️⃣ Social Proof Dominates

•	Nearly 47% of predictive power comes from Votes.

This suggests:

•	Engagement volume strongly stabilizes ratings.

•	Restaurants with more reviews tend to achieve higher and more reliable ratings.

2️⃣ Market Structure Matters

•	City_freq, Latitude, and Longitude collectively contribute ~29% importance.

Ratings are partially shaped by:

•	Geographic clustering

•	Market competitiveness

•	Regional customer behavior

3️⃣ Price Is Secondary

While pricing contributes, it plays a smaller role than engagement and location.

🧠 What This Project Demonstrates

•	Structured EDA workflow

•	Careful leakage prevention

•	Handling high-cardinality categorical variables

•	Nonlinear modeling with ensemble methods

•	Hyperparameter tuning

•	Feature importance interpretation

🎯 Final Insight

Restaurant ratings are not random. They are driven primarily by:

•	Social validation (Votes)

•	Geographic dynamics

•	Market density, and to a lesser extent, pricing signals

This project shows how machine learning can extract structural drivers of customer perception from marketplace data.
 used for inference:

model = joblib.load("model.pkl")
