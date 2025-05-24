# Bike Sharing Demand Prediction

This project predicts hourly bike rental demand using a variety of weather, time, and seasonal features. The goal is to accurately forecast the number of bike rentals to help optimize resource allocation for bike sharing services.

---

## Dataset

The dataset contains hourly bike rental records with features including:

- Date and time (`date`, `hour`)
- Weather conditions (`temperature`, `humidity`, `windspeed`, etc.)
- Seasonal information (`season`, `holiday`, `workingday`)
- Target variable: number of bike rentals (`count`)

---

## Data Processing

- Extracted time features from the `date` column: `day`, `month`, `weekday`, and `is_weekend`.
- One-hot encoded categorical features like `season` and `holiday`.
- Scaled numerical features using `StandardScaler` to normalize distributions.
- Split the data into training (80%) and testing (20%) sets to evaluate model generalization.

---

## Modeling

- Tested several regression models:
  - Linear Regression
  - Random Forest Regressor
  - XGBoost Regressor (best performance)
- Used `RandomizedSearchCV` to tune hyperparameters of the XGBoost model.
- The final XGBoost model achieved an R² score of approximately **0.94** on the test set, indicating strong predictive accuracy.

---

## Evaluation Metrics

- **R² Score:** Measures how well the model explains variance in rental demand.
- **Mean Squared Error (MSE):** Average squared difference between predicted and actual counts.
- Additional metrics such as RMSE or MAE can be computed for interpretability.

---

## Usage

1. Clone the repo.
2. Install requirements:
   ```bash
   pip install -r requirements.txt
3. Run model_training.py to preprocess data, train the model, and save the best model pipeline.
4. Use predict.py (or equivalent script) to load the model and predict bike rental demand on new data.

---

## Insights
-Time features (hour of day, weekend/weekday) strongly influence rental patterns.
-Weather conditions (temperature, humidity, windspeed) impact user behavior.
-Seasonal effects captured via one-hot encoding improve model accuracy.
-Feature importance analysis from XGBoost reveals the top drivers of rental demand.

---

## Future Work
-Incorporate lagged demand features to capture temporal dependencies.
-Explore advanced models like LightGBM or CatBoost.
-Use SHAP values for model explainability.
-Experiment with time-series cross-validation to better simulate real-world forecasting.

---

## References
-Dataset source: https://www.kaggle.com/datasets/saurabhshahane/seoul-bike-sharing-demand-prediction
-XGBoost documentation: https://xgboost.readthedocs.io/
-Scikit-learn documentation: https://scikit-learn.org/stable/
