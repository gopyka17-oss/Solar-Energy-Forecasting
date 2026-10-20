# ☀️ Solar Energy Forecasting Using Machine Learning

### A Comparative Study of Linear Regression and Random Forest with Chronological Evaluation

This project develops and evaluates machine learning models for predicting solar energy generation using historical weather observations and temporal information.

The study compares **Linear Regression** and **Random Forest Regression** against a simple baseline, using a chronological train-test split to evaluate model performance on later observations.

**Best-performing model: Random Forest Regression (R² = 0.9011, RMSE = 329.21 Wh).**

---

## 1. Project Overview

Solar energy generation is influenced by environmental conditions such as sunlight intensity, temperature, rainfall, cloud coverage, and daylight duration.

Accurate estimation of solar energy output can support renewable energy planning, resource management, and data-driven decision-making.

This project investigates how effectively supervised machine learning algorithms can estimate solar energy generation from weather-related measurements.

### Objectives

- Explore historical solar energy and weather data.
- Clean and preprocess timestamped observations.
- Investigate relationships between environmental variables and solar energy generation.
- Develop Linear Regression and Random Forest prediction models.
- Evaluate model performance using a chronological holdout dataset.
- Compare the models against a training-mean baseline.
- Analyze prediction errors and important explanatory features.
- Demonstrate a hypothetical January 2026 energy-generation scenario.

## 2. Dataset

The dataset contains historical solar energy and weather measurements recorded between **January 2017 and August 2022**.

| Dataset property | Description |
|---|---|
| Original observations | 196,777 |
| Cleaned observations | 196,768 |
| Number of original columns | 7 |
| Temporal resolution | Predominantly 15-minute intervals |
| Target variable | Energy Captured [Wh] |
| Data format | Excel (.xlsx) |

### Original Dataset Features

| Feature | Description |
|---|---|
| Time | Timestamp of observation |
| Energy Captured[Wh] | Solar energy captured, measured in Wh |
| Sun Light Intensity (W/m2) | Measured solar radiation intensity |
| Temperature | Recorded temperature |
| 1 Hour Rain Fall | Rainfall measurement |
| Cloud Coverage | Recorded cloud coverage |
| Length of Day_Light | Daylight-duration measurement |

Additional calendar-based features are derived from the timestamps during preprocessing.

**Data quality:** The original dataset contained eight missing timestamps and one exact duplicate timestamp record. These records were removed, and the remaining observations were sorted chronologically.

The time series also contains some irregular intervals, so observations should not be assumed to form a perfectly continuous 15-minute sequence.

## 3. Technologies Used

- **Python** — Programming language
- **Pandas** — Data manipulation and preprocessing
- **NumPy** — Numerical computation
- **Matplotlib and Seaborn** — Data visualization
- **Scikit-learn** — Machine learning and evaluation
- **Google Colab / Jupyter Notebook** — Development environment

## 4. Methodology

The project follows a structured machine learning workflow.

**Step 1: Data Loading**

Import the Excel dataset and inspect its dimensions, columns, data types, and timestamp coverage.

**Step 2: Exploratory Data Analysis**

Examine the distributions and relationships among solar energy generation, weather variables, and temporal patterns.

**Step 3: Data Preprocessing**

- Convert timestamps into datetime format.
- Remove observations with missing timestamps.
- Remove exact duplicate records.
- Sort observations chronologically.
- Prepare the dataset for modeling.

**Step 4: Feature Engineering**

Extract relevant calendar information from timestamps and combine it with weather measurements to construct model inputs.

**Step 5: Chronological Train-Test Split**

Divide the observations into earlier training data and later testing data, rather than randomly shuffling the time series.

This provides a more appropriate evaluation for temporally ordered observations.

**Step 6: Model Development**

Train and compare two supervised regression algorithms:

- Linear Regression
- Random Forest Regression

A training-mean baseline is also evaluated to provide a simple reference point.

**Step 7: Model Evaluation**

Evaluate prediction accuracy using:

- R² (Coefficient of Determination)
- Mean Absolute Error (MAE)
- Mean Squared Error (MSE)
- Root Mean Squared Error (RMSE)

**Step 8: Prediction Analysis**

Examine actual versus predicted values, residual errors, and model feature importance.

**Step 9: January 2026 Scenario**

Generate a hypothetical energy estimate using assumptions derived from historical weather conditions.

This is a scenario analysis, not a verified forecast of actual January 2026 generation.

## 5. Model Performance

The following results were obtained on the chronological holdout test set.

| Model | R² | MAE (Wh) | MSE (Wh²) | RMSE (Wh) |
|---|---:|---:|---:|---:|
| Training-mean baseline | -0.0008 | 765.1099 | 1,096,383 | 1047.0831 |
| Linear Regression | 0.8249 | 262.1231 | 191,850.1 | 438.0070 |
| **Random Forest** | **0.9011** | **131.6503** | **108,375.9** | **329.2050** |

### Best Model: Random Forest Regression

Random Forest achieved the strongest predictive performance among the evaluated machine learning models.

Key findings:

- **R² of 0.9011:** Approximately 90.11% of the variation in held-out solar energy observations was explained by the model.
- **MAE of 131.65 Wh:** The average absolute prediction error was approximately 131.65 Wh.
- **RMSE of 329.21 Wh:** Random Forest achieved the lowest root mean squared error.
- **24.8% lower RMSE** compared with Linear Regression.
- **68.6% lower RMSE** compared with the training-mean baseline.

These findings indicate that Random Forest captures relationships in the observed data more effectively than the linear model.

## 6. Visualizations and Analysis

The notebook includes exploratory and model-evaluation visualizations to support interpretation of the dataset and prediction results.

The analysis covers:

- Historical solar energy and weather patterns
- Relationships among input variables
- Actual versus predicted solar energy values
- Prediction errors and residuals
- Model performance comparison
- Random Forest feature importance

## 7. January 2026 Scenario Analysis

The project includes a hypothetical January 2026 solar energy estimation exercise based on historical January weather assumptions.

**Important distinction:** The dataset ends in August 2022. Actual January 2026 weather observations are not available in the historical training dataset.

Therefore, the January 2026 estimates represent model-generated outcomes under assumed weather conditions rather than independently validated future forecasts.

A real operational forecasting system would require appropriate future weather forecasts, a clearly defined forecast horizon, and further time-series validation.

## 8. How to Run the Project

### Option 1: Google Colab

1. Open [Google Colab](https://colab.research.google.com/).
2. Upload `Solar_Energy_Forecasting.ipynb`.
3. Run the notebook cells in sequence.
4. Upload the original Excel dataset when prompted.
5. Review the generated visualizations, evaluation metrics, and scenario results.

### Option 2: Local Jupyter Notebook

Install the required Python packages:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl jupyter
```

Launch Jupyter:

```bash
jupyter notebook
```

Open the notebook and adjust the dataset-loading step if necessary to point to your local Excel file.

## 9. Limitations

Although Random Forest achieved promising results, several limitations should be considered.

1. **Weather input availability:** The evaluation uses recorded weather measurements. Operational future forecasting would require weather predictions or inputs available at the intended prediction time.
2. **Historical coverage:** The dataset covers January 2017 to August 2022, limiting conclusions about more recent conditions.
3. **Temporal irregularities:** The dataset contains some missing intervals and irregular timestamp gaps.
4. **Model generalization:** Performance on one chronological holdout does not guarantee equivalent accuracy across all seasons or future years.
5. **Scenario uncertainty:** The January 2026 analysis is based on historical assumptions rather than actual future meteorological observations.

## 10. Future Improvements

Potential extensions include:

- Walk-forward or rolling-origin time-series validation
- Hyperparameter optimization
- Gradient Boosting and XGBoost comparisons
- Weather forecast integration
- Timestamp-aware lag and rolling-window features
- Seasonal error analysis
- Model explainability using SHAP
- A dashboard for visualizing solar energy estimates

These are proposed improvements and are not claimed as implemented features of the current notebook.

## 11. Conclusion

This project demonstrates the application of supervised machine learning to solar energy estimation using historical weather and temporal data.

Random Forest Regression outperformed Linear Regression and the training-mean baseline, achieving an R² score of **0.9011** and an RMSE of **329.21 Wh** on the chronological holdout dataset.

The findings highlight the potential of nonlinear ensemble methods for modeling relationships between environmental conditions and solar energy generation, while also emphasizing the importance of temporal evaluation and careful interpretation of future prediction scenarios.

---

## Author

**Gopika P**

MSc Data Science & Analytics  
Mahatma Gandhi University, Kerala, India

**GitHub:** [gopyka17-oss](https://github.com/gopyka17-oss)

**LinkedIn:** [Gopika P](https://www.linkedin.com/in/gopika-p-2b97a1351/)

---

*Project focus: Machine Learning · Regression · Renewable Energy Analytics · Data Science · Temporal Evaluation*
