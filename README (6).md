
# Optimizing Air Travel: A Data-Driven Approach to Flight Delay Analysis & Prediction

## 🚀 Project Overview

Airline delays cost passengers time and airlines money. This project leverages historical flight data to:

- Explore delay patterns and root causes via EDA  
- Build & compare regression models to predict (a) whether a flight will be delayed and (b) its expected delay in minutes  
- Identify the top operational drivers of delay  
- Recommend data-driven interventions to reduce future delays  

## ⚙️ Installation

```bash
git clone https://github.com/payalkanyan/AirTravelDelayPred
cd air-travel-delay-analysis
python3 -m venv .venv
source .venv/bin/activate      # Linux/macOS
.venv\Scripts\activate         # Windows

pip install -r requirements.txt
```

**Key libraries:** `pandas`, `numpy`, `scikit-learn`, `xgboost`, `lightgbm`, `catboost`, `matplotlib`, `seaborn`, `shap`

## ▶️ Usage

1. Download `Airline_Delay_Cause.csv` into the project root.
2. Launch the notebook:

   ```bash
   jupyter lab
   ```

   or

   ```bash
   jupyter notebook
   ```
3. Run all cells in `AirTravelPred.ipynb` in order. Sections include:

   * Data Loading & Cleaning
   * Exploratory Data Analysis
   * Feature Engineering
   * Model Training (regression & classification)
   * Evaluation & Comparison
   * Feature Importance & Insights
   * Actionable Recommendations
   * Project Summary & Next Steps

## 🎯 Key Results

| Model             |   MAE |  RMSE |    R² | F₂ (clf) |
| ----------------- | ----: | ----: | ----: | -------: |
| LightGBMBoost     | 0.036 | 0.035 | 0.963 |     0.63 |
| XGBoost           | 0.031 | 0.031 | 0.986 |     0.63 |
| CatBoost          | 0.032 | 0.035 | 0.963 |     0.73 |
| KNN               | 0.062 | 0.047 | 0.949 |     0.85 |
| Stacking          | 0.034 | 0.013 | 0.986 |     0.88 |
| Random Forest     | 0.035 | 0.014 | 0.985 |     0.93 |
| Linear Regression | 0.040 | 0.020 | 0.983 |     0.94 |
| MLP               | 0.029 | 0.009 | 0.990 |     0.97 |

* Top regressors achieve sub-1 minute MAE on scaled delays
* Classification F₂-scores (\~0.80) emphasize recall of delayed flights

## 🔍 Actionable Insights & Recommendations

1. **Late Aircraft Turnaround (\~32% importance)**

   * Add 5–10 min gate buffers on high-traffic routes
   * Deploy rapid deboarding crews

2. **Carrier-Related Delays (\~24%)**

   * Optimize crew scheduling using delay-risk forecasts
   * Prioritize overnight maintenance

3. **NAS & Weather Delays (\~29% combined)**

   * Integrate live FAA advisories and METAR/TAF feeds
   * Build proactive re-routing logic

4. **Security Delays (\~7%)**

   * Ramp up TSA staffing during holiday peaks
   * Pilot automated screening lanes

## 🔭 Next Steps & Future Work

* Augment data sources with gate-utilization, real-time weather, ATC congestion, and aircraft-type info
* Real-time deployment: expose the stacking model via REST API for pre-pushback delay alerts
* Causal evaluation: conduct A/B tests or synthetic-control studies to quantify intervention impact
* Automated monitoring: build a dashboard to track drift in MAE/RMSE and F₂, schedule monthly retraining

