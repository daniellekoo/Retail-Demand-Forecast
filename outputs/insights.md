# Key Insights & Takeaways

This document summarizes the key insights derived from comparing baseline forecasts and machine learning models in this project.  
The goal was not only to improve predictive performance, but also to understand *why* certain approaches worked better than others.

---

## 1. Why the Baseline Model Outperformed ML Models

The provided **Demand Forecast** baseline significantly outperformed all machine learning models across RMSE, MAE, and RMSLE.

This result suggests that the baseline forecast was not a naive statistical estimate, but rather a **production-grade signal** likely incorporating additional information that was not present in the dataset used for modeling.  
Examples of such information may include historical demand smoothing, domain-specific heuristics, supply chain constraints, or external business signals.

In other words, the baseline appears to represent a **downstream, business-optimized forecast**, while the ML models were trained only on the limited features available in the dataset.  
As a result, the baseline had access to richer and more structured information, leading to superior performance.

---

## 2. Why Machine Learning Models Did Not Perform as Well

Despite experimenting with multiple models (Linear Regression, Random Forest, LightGBM), performance improvements were limited.

Several factors contributed to this outcome:

- **Feature limitations**: The dataset mainly contained operational variables (inventory level, price, discounts, calendar features) but lacked high-impact demand drivers such as promotions strategy, marketing spend, or macro-level signals.
- **Target leakage risk avoidance**: Care was taken to avoid using future information, which limited the usable feature set and reduced apparent performance gains.
- **High dominance of inventory-related signals**: Feature importance analysis showed that *Inventory Level* overwhelmingly dominated predictions, making it difficult for other features to meaningfully improve accuracy.
- **Aggregation trade-offs**: Weekly aggregation reduced noise and improved stability in some cases, but it also removed short-term variability that the baseline forecast may already capture effectively.

Overall, the ML models were constrained by the **information ceiling of the dataset**, rather than model capacity or tuning choices.

---

## 3. What This Project Demonstrated and What Was Learned

This project highlighted an important real-world lesson:

> **A strong baseline can outperform sophisticated ML models when it embeds domain knowledge and additional signals that data scientists do not have access to.**

Key takeaways include:

- Model performance should always be evaluated **relative to baselines**, not in isolation.
- Feature engineering and data availability often matter more than model complexity.
- ML is not guaranteed to outperform existing systems, especially when baselines are production-optimized.
- Understanding *why* a model fails to outperform a baseline is as valuable as improving metrics.

From a practical standpoint, this project reinforced the importance of combining **business context, data understanding, and modeling discipline** rather than relying solely on algorithmic complexity.

---

## Final Reflection

Rather than treating the baseline as a competitor to beat, this project reframed it as a **benchmark that reveals the limits of the available data**.  
The analysis demonstrates analytical maturity by recognizing when ML adds value — and when it does not — which is a critical skill in applied data science.
