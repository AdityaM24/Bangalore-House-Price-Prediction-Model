# Bangalore-House-Price-Prediction-Model
This ML model uses Linear Regression to predict house prices in Bangalore. It considers factors like location, size, bedrooms and bathrooms, offering accurate and interpretable price estimates. A simple yet effective tool for real estate market analysis and decision-making.

# 1. Data Import and Initial Exploration
Libraries Imported: pandas, numpy, seaborn, matplotlib are imported for data manipulation, visualization, and plotting.

Dataset Loaded: The dataset, named bengaluru_house_prices(df).csv, is read into a DataFrame named df1.

Initial Exploration: The dataset's structure (shape) and unique values for columns like area_type are explored.
Irrelevant columns (area_type, society, balcony, availability) are dropped to focus on core features.

# 2. Data Cleaning
Handling Missing Values: Rows with missing values are dropped to create a cleaned DataFrame (df3).

Feature Engineering: 'size' column is processed to extract the number of bedrooms (bhk).
The total_sqft column is cleaned to handle ranges (e.g., "2000-3000") and non-numeric values, converting them into numerical values.

# 3. New Feature Creation:
A column price_per_sqft is calculated for deeper analysis of price trends.

# 4. Model Training and Evaluation
Data Splitting: The dataset is split into training and testing sets using train_test_split from sklearn.

Linear Regression Model: A LinearRegression model is trained on the data.
Model performance is evaluated using score on the test set.

Cross-Validation: Cross-validation is performed using ShuffleSplit to assess the model's robustness over different data splits.

# 5. Finding the Best Model
The notebook uses GridSearchCV to identify the optimal regression model. Models tested include:

Linear Regression: Implemented using a pipeline that includes feature scaling (StandardScaler).
Hyperparameters like fit_intercept are tuned.

Lasso Regression: Regularization strength (alpha) and selection method (random or cyclic) are evaluated.

Decision Tree Regressor: Hyperparameters such as criterion and max_depth are tested for optimization.

-> A function (find_best_model_using_gridsearchcv) encapsulates the model selection process. It:
      a. Tests multiple algorithms.
      b. Tunes hyperparameters using a grid search approach.
      c. Returns the best model and parameters for the given dataset.

# 6. Property Price Prediction Function
The predict_price function predicts the property price by utilizing the trained linear regression model and the following input features:
i) location: Encodes the location by finding the corresponding column index in the feature set (X.columns).
Marks the encoded location column in the input feature vector.
ii) sqft: Represents the total square footage of the property.
iii) bath: Specifies the number of bathrooms in the property.
iv) bhk: Indicates the number of bedrooms (or BHK units) in the property.
