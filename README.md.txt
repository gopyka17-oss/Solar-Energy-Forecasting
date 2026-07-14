<div align="center">

# ☀️ Weather-Driven Solar Energy Forecasting Using Machine Learning

### End-to-End Time-Series Forecasting and Renewable Energy Analytics Project

![Python](https://img.shields.io/badge/Python-3.13-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-black?logo=pandas)
![NumPy](https://img.shields.io/badge/NumPy-Scientific%20Computing-blue?logo=numpy)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Machine%20Learning-orange?logo=scikitlearn)
![Time Series](https://img.shields.io/badge/Time-Series%20Forecasting-purple)
![License](https://img.shields.io/badge/License-MIT-green)

</div>

---

## 📌 Project Overview

Solar energy production changes continuously because of weather conditions, seasonal patterns, daylight duration, and time of day.

This project develops an end-to-end machine learning pipeline to forecast solar energy output using historical solar production and weather data recorded at 15-minute intervals.

The project covers:

- Data cleaning
- Exploratory Data Analysis
- Time-based feature engineering
- Lag and rolling features
- Chronological train-test splitting
- Regression model comparison
- Forecast visualization
- Feature importance analysis
- Renewable energy planning insights

---

## ⭐ Project Highlights

- Analysed approximately **196,000 time-series observations**
- Used weather and time variables to forecast solar output
- Created lag features for previous 15-minute, 1-hour, and 24-hour energy production
- Created rolling averages to capture short-term and daily trends
- Compared three regression models
- Achieved an **R² score of 0.9602**
- Saved the best-performing model for future deployment
- Generated forecast and feature-importance visualizations

---

## 🎯 Project Objective

The main objective is to predict:

```text
Energy Captured [Wh]
```

using variables such as:

- Sunlight Intensity
- Temperature
- Rainfall
- Cloud Coverage
- Daylight Length
- Hour
- Month
- Previous Energy Output
- Rolling Average Energy

The predictions can support:

- Energy-storage planning
- Grid balancing
- Renewable-energy scheduling
- Capacity estimation
- Operational decision-making

---

## 📂 Dataset

**Source file:** `solar_weather - Raw - Assignment Oct 2025-1.xlsx`

The dataset contains approximately:

```text
196,777 rows
7 original columns
```

### Original variables

| Variable | Description |
|---|---|
| Time | Date and time of observation |
| Energy Captured[Wh] | Solar energy output and prediction target |
| Sun Light Intensity (W/m2) | Measured sunlight intensity |
| Temperature | Recorded temperature |
| 1 Hour Rain Fall | Rainfall during the previous hour |
| Cloud Coverage | Percentage of cloud coverage |
| Length of Day_Light | Daylight duration |

---

## 🛠 Technologies Used

| Category | Tools and Libraries |
|---|---|
| Programming Language | Python |
| Data Processing | Pandas, NumPy |
| Data Visualization | Matplotlib, Seaborn |
| Machine Learning | Scikit-learn |
| Models | Linear Regression, Random Forest, Gradient Boosting |
| Model Saving | Joblib |
| Excel Processing | OpenPyXL |

---

## 🔄 Project Workflow

```text
Raw Solar and Weather Dataset
              │
              ▼
Data Cleaning and Validation
              │
              ▼
Datetime Processing
              │
              ▼
Exploratory Data Analysis
              │
              ▼
Time-Based Feature Engineering
              │
              ▼
Lag and Rolling Features
              │
              ▼
Chronological Train-Test Split
              │
              ▼
Regression Model Training
              │
              ▼
Model Evaluation and Comparison
              │
              ▼
Best Model Selection
              │
              ▼
Forecast Visualization and Insights
```

---

## 🧹 Data Cleaning

The preprocessing stage included:

- Converting numeric columns stored as text into numeric values
- Handling missing values using forward filling
- Converting the `Time` column into datetime format
- Clipping cloud coverage to the valid range of 0–100%
- Removing rows affected by lag and rolling calculations
- Saving a cleaned and processed dataset

After preprocessing and feature engineering, the dataset contained:

```text
196,673 rows
17 columns
```

---

## 🧠 Feature Engineering

### Time-based features

- Year
- Month
- Day
- Hour
- Minute

### Lag features

| Feature | Meaning |
|---|---|
| Lag_1 | Energy output 15 minutes earlier |
| Lag_4 | Energy output 1 hour earlier |
| Lag_96 | Energy output 24 hours earlier |

### Rolling features

| Feature | Meaning |
|---|---|
| Rolling_4 | Average energy during the previous hour |
| Rolling_96 | Average energy during the previous 24 hours |

These features help the models learn daily cycles, short-term changes, and repeating solar-production patterns.

---

## ⏳ Time-Series Train-Test Split

The dataset was split chronologically rather than randomly.

```text
First 80% of observations → Training data
Last 20% of observations  → Testing data
```

This prevents future data from leaking into the training set and better represents real forecasting conditions.

---

## 🤖 Machine Learning Models

The following regression models were trained and compared:

- Linear Regression
- Random Forest Regressor
- Gradient Boosting Regressor

---

## 📈 Model Performance

| Model | MAE | RMSE | R² | MAPE |
|---|---:|---:|---:|---:|
| Linear Regression | 114.21 | 230.94 | 0.9513 | 1741.79% |
| **Random Forest** | **79.54** | **208.87** | **0.9602** | **85.88%** |
| Gradient Boosting | 89.11 | 215.87 | 0.9575 | 338.70% |

---

## 🏆 Best Model

The **Random Forest Regressor** achieved the strongest overall performance.

```text
MAE: 79.54 Wh
RMSE: 208.87 Wh
R²: 0.9602
```

The model explains approximately **96.02% of the variation** in solar energy output.

The MAPE values are less reliable because the dataset contains many zero-energy observations, particularly during nighttime periods. For this reason, MAE, RMSE, and R² are more useful for evaluating this project.

---

## 📊 Actual vs Predicted Energy

![Actual vs Predicted](images/actual_vs_predicted.png)

The forecast closely follows the observed energy-production pattern, including changing levels of solar output over time.

---

## 📈 Solar Energy Forecast

![Solar Forecast](images/solar_forecast.png)

This chart compares actual and predicted solar-energy output across the test period.

---

## ⭐ Feature Importance

![Feature Importance](images/feature_importance.png)

The feature-importance analysis shows which weather, time, and historical-energy variables contribute most strongly to the Random Forest predictions.

Typical high-impact variables include:

- Sunlight Intensity
- Recent Energy Output
- Rolling Energy Averages
- Hour of Day
- Cloud Coverage
- Daylight Length

---

## 💡 Key Insights

- Solar-energy production is strongly influenced by sunlight intensity.
- Recent production values are highly useful for short-term forecasting.
- Rolling averages help capture daily and hourly trends.
- Cloud coverage generally reduces solar output.
- Daylight duration and hour of day help explain seasonal and intraday variation.
- Random Forest performs better than Linear Regression because it captures nonlinear relationships between weather and energy production.

---

## 🏭 Business and Operational Applications

This forecasting system can support:

- Battery-storage scheduling
- Energy-demand planning
- Grid-balancing decisions
- Backup-power preparation
- Renewable-energy capacity management
- Maintenance and operational planning

More accurate forecasts can help energy operators reduce waste and improve reliability.

---

## 📁 Repository Structure

```text
Solar-Energy-Forecasting/
│
├── data/
│   └── solar_weather.xlsx
│
├── images/
│   ├── actual_vs_predicted.png
│   ├── feature_importance.png
│   └── solar_forecast.png
│
├── models/
│   └── best_solar_model.pkl
│
├── notebooks/
│
├── processed_data/
│   └── processed_solar_dataset.csv
│
├── results/
│   ├── model_comparison.csv
│   ├── feature_importance.csv
│   └── final_metrics.csv
│
├── src/
│   └── solar_energy_prediction.py
│
├── README.md
├── requirements.txt
├── LICENSE
└── .gitignore
```

---

## 🚀 Installation and Usage

Clone the repository:

```bash
git clone https://github.com/gopyka17-oss/Solar-Energy-Forecasting.git
```

Move into the project folder:

```bash
cd Solar-Energy-Forecasting
```

Install the required packages:

```bash
pip install -r requirements.txt
```

Run the forecasting script:

```bash
python src/solar_energy_prediction.py
```

---

## 📁 Generated Outputs

The project generates:

- Processed solar dataset
- Model-comparison results
- Final model metrics
- Feature-importance data
- Actual-vs-predicted visualization
- Solar forecast visualization
- Saved Random Forest model

---

## 🎯 Skills Demonstrated

- Time-Series Data Analysis
- Data Cleaning
- Datetime Processing
- Feature Engineering
- Lag Features
- Rolling Statistics
- Regression Modelling
- Chronological Validation
- Model Evaluation
- Forecast Visualization
- Renewable Energy Analytics
- Python Programming

---

## 🔮 Future Improvements

- Add XGBoost and LightGBM regressors
- Use time-series cross-validation
- Add prediction intervals
- Include recent weather data
- Build a Streamlit solar forecasting dashboard
- Add a 24-hour production forecast
- Deploy the dashboard online
- Compare against ARIMA, Prophet, and LSTM models

---

## 👩‍💻 Author

**Gopika Prasanna**  
MSc Data Science & Analytics  
Aspiring Data Analyst / Data Scientist  

Skills: Python • SQL • R • Machine Learning • Data Analytics

---

⭐ If you found this project useful, consider giving it a star.