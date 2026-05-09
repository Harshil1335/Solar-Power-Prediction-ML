# ☀️ Solar Power Generation Prediction Model

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.0%2B-orange)
![XGBoost](https://img.shields.io/badge/XGBoost-1.7%2B-green)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Latest-yellow)

## 📌 Project Overview
The integration of solar photovoltaic (PV) energy into the power grid is complicated by its inherent volatility due to changing weather conditions. This project addresses the "duck curve" and grid intermittency challenges by developing highly accurate, data-driven forecasting models. 

By evaluating both Ensemble Machine Learning (XGBoost, Random Forest) and Deep Learning (LSTM) architectures, this project predicts short-term DC Power generation based on localized weather sensor readings.

## 📊 Dataset
The data utilized comprises 34 days of continuous operational records from two distinct solar power plants in India, recorded at 15-minute intervals.
* **Target Variable:** `DC_POWER`
* **Primary Features:** `IRRADIATION`, `AMBIENT_TEMPERATURE`, `MODULE_TEMPERATURE`
* **Engineered Features:** Temporal Lags (`lag_1`, `lag_24`), Rolling Means, Time Decomposition (`Hour`, `Day of Year`).

**Data Source:** [Kaggle - Solar Power Generation Data](https://www.kaggle.com/datasets/anikannal/solar-power-generation-data)

## 🛠️ Methodology & Tech Stack
1. **Data Preprocessing:** Inner-join synchronization of inverter generation logs with plant-level weather sensors. Removal of zero-generation nighttime data to prevent artificial accuracy inflation.
2. **Feature Engineering:** Implementation of sliding temporal windows and lag features to provide models with sequence momentum. Data scaled using Min-Max Normalization.
3. **Model Architectures:**
   * **Linear Regression** (Statistical Baseline)
   * **Random Forest Regressor** (Ensemble Bagging)
   * **Extreme Gradient Boosting (XGBoost)** (Sequential Error Correction)
   * **Long Short-Term Memory (LSTM)** (Deep Learning RNN for time-series)

## 🏆 Model Performance & Results
Models were evaluated on an unseen testing subset. **XGBoost** proved to be the optimal model for instantaneous point prediction precision, while the **LSTM** successfully captured the diurnal sequential "bell curve" of the sun's trajectory.

| Model | RMSE (Lower is Better) | MAE (Lower is Better) | R² Score (Higher is Better) |
| :--- | :--- | :--- | :--- |
| **Linear Regression** | 487.71 | 303.68 | 0.9806 |
| **Random Forest** | 449.24 | 250.41 | 0.9835 |
| **XGBoost** | **445.91** | **244.36** | **0.9837** |
| **LSTM** | 735.36 | 445.58 | 0.9559 |

### Visualizations
*(Note: Upload your graph images to a folder named `images/` in your repo to display them here)*
* ![Model Comparison](images/model_comparison_bar.png)
* ![Actual vs Predicted](images/actual_vs_predicted_all.png)

## 🚀 Installation & Usage

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/your-username/Solar-Power-Prediction-ML.git](https://github.com/your-username/Solar-Power-Prediction-ML.git)
   cd Solar-Power-Prediction-ML
