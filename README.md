# Retail-Demand-Forecast
Demand forecasting using baseline and ML models

## Project Overview
This project started from a simple question:

**“Can machine learning models actually outperform an existing demand forecast?”**

Using a retail sales dataset, I compared a provided baseline demand forecast with several machine learning models.  
Rather than focusing only on improving accuracy, I focused on **model comparison, feature behavior, and validation logic**, which are closer to real-world analytics work.

The project documents not only what worked, but also what *did not* work — and why.

---

## What I Tried
1. Verified baseline performance to establish a realistic benchmark  
2. Built multiple ML models and compared their performance
3. Tried to improve Linear Regression with lag features
4. Tested whether limiting or expanding feature scope affected model results
5. Analyzed feature importance to understand demand drivers
6. Visualized results using Python and Tableau

---

## Models Used
- Baseline: Provided Demand Forecast
- Linear Regression (no lag)
- Linear Regression (with lag features)
- Random Forest
- LightGBM (daily data)
- LightGBM (weekly aggregated data)

---

## Evaluation Metrics
- RMSE
- MAE
- RMSLE  

All models were evaluated using **time-based splits** to avoid data leakage.

---

## Key Results
| Model | RMSE | MAE |
|------|------|-----|
| Baseline (Demand Forecast) | **~10** | **~8** |
| Linear Regression | ~88 | ~69 |
| Random Forest | ~89 | ~70 |
| LightGBM (Daily) | ~97 | ~73 |
| LightGBM (Weekly) | ~273 | ~207 |

---

## What I Observed
- The provided baseline significantly outperformed all ML models.
- Adding lag features improved Linear Regression slightly, but not enough to close the gap.
- Expanding from a restricted feature scope to the full dataset produced **very similar results**, suggesting that performance was not highly dependent on column selection.
- Weekly aggregation stabilized model behavior but still did not outperform the baseline.

This strongly suggests that the baseline forecast likely incorporates **additional domain knowledge or external signals** that were not available in the dataset.

---

## Feature Importance Insights
Across models, the most influential features were:
- Inventory Level
- Recent sales behavior (lag and rolling features)
- Units Ordered
- Price and Competitor Pricing

Interestingly, promotion- or season-related variables had relatively smaller impact.

**From a business perspective**, this indicates that demand in this dataset is driven more by **inventory availability and recent sales momentum** than by calendar-based factors.

---

## Visualization
- Python was used for model diagnostics and feature importance plots.
- Tableau dashboards were created to compare:
  - Baseline vs ML performance
  - Daily vs Weekly modeling
  - Feature importance rankings

---

## Key Takeaways
- A strong operational baseline can outperform complex ML models.
- Machine learning does not automatically guarantee better results.
- Feature engineering improves interpretability, even when accuracy gains are limited.
- Model evaluation should prioritize **validation logic and business context**, not just metrics.

---

## Tools
- Python (pandas, numpy, scikit-learn, LightGBM)
- Jupyter Notebook
- Tableau
- GitHub

