# New York City Taxi Fare Prediction

**Project Overview:**

This project focuses on predicting taxi fares in New York City using a supervised machine learning approach. The dataset, sourced from Kaggle's [New York City Taxi Fare Prediction competition](https://www.kaggle.com/competitions/new-york-city-taxi-fare-prediction), presents a challenging regression problem due to its large size and inherent data noise.

**Key Achievements:**

- Achieved an RMSE (Root Mean Squared Error) of 3.15, placing the model in the 83rd percentile on the Kaggle leaderboard. (Note: The best model achieved an RMSE of 1.38).
- Successfully handled a large dataset (55 million rows) by strategically sampling 1% (550,000 rows) for efficient processing and model development.
- Implemented robust data cleaning and feature engineering techniques to significantly improve model accuracy.

**Data:**

- The original dataset contained approximately 55 million rows.
- To manage computational resources, a 1% sample (550,000 rows) was used for training and validation.
- The sampled data was split into training (80%) and validation (20%) sets.

**Exploratory Data Analysis (EDA):**

- Initial EDA on the 'fare_amount' column (using a 20,000 sample) revealed a roughly normal distribution, with the highest frequency of fares between $5 and $6.
- Identified significant data noise, including outliers like extremely high fare amounts (e.g., $6250).

**Data Cleaning and Noise Reduction:**

- **Missing Value Handling:** Removed rows with missing values.
- **Passenger Count Validation:** Eliminated rows where 'passenger_count' was less than 1.
- **Geographical Outlier Removal:** Filtered out rows with latitude values outside the range of -90 to 90 and longitude values outside the range of -180 to 180.

**Feature Engineering:**

- **Datetime Feature Extraction:** Converted the 'pickup_datetime' column to datetime objects and extracted 'Day', 'Month', 'DayOfWeek', and 'Year' features.
- **Distance Calculation (Haversine Formula):** Calculated the distance between pickup and dropoff coordinates using the Haversine formula, providing a crucial feature for fare prediction.
- **Location Density/Busy Locations:** Identified and encoded major/busy locations based on latitude and longitude ranges, reflecting the impact of location density on fare amounts.

**Model Development and Evaluation:**

The following models were explored and evaluated using RMSE:

1.  **Ridge Regression:**
    -   RMSE: 5.5
    -   Note: Performed poorly due to the non-linear nature of the data.
2.  **Decision Tree:**
    -   RMSE: 4.2
    -   Hyperparameters: `max_depth=8` (to prevent overfitting).
3.  **Random Forest:**
    -   RMSE (Train): 1.38
    -   RMSE (Validation): 3.5
    -   Hyperparameters: `max_depth=10`, `n_features=0.8` (to reduce overfitting and improve generalization).
4.  **XGBoost (Final Model):**
    -   RMSE: 3.07
    -   Hyperparameters: `learning_rate=0.09`, `n_estimators=500` (optimized for performance).

**Conclusion:**

XGBoost was selected as the final model due to its superior performance, achieving the lowest RMSE of 3.07 on the validation set. The project demonstrates the importance of thorough data cleaning, feature engineering, and hyperparameter tuning in achieving accurate predictions for complex datasets.

**Future Improvements:**

-   Explore more advanced feature engineering techniques, such as incorporating weather data or traffic information.
-   Experiment with other advanced models like LightGBM or CatBoost.
-   Fine-tune hyperparameters further using techniques like Bayesian optimization.
-   Consider using a larger portion of the dataset if computational resources allow.

**GitHub Repository:**

[Link to your GitHub Repository](https://github.com/Ganesh-reddy005/NYC-taxi-fare-prediction)

**Dependencies:**

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn(for models)
