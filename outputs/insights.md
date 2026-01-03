# Key Insights

This section summarizes what was learned from comparing baseline forecasts and machine learning models in this project.  
Rather than focusing only on model performance, the goal was to understand why certain approaches worked better than others.

## Why the Baseline Performed Better

The provided Demand Forecast baseline clearly outperformed all machine learning models across RMSE, MAE, and RMSLE.

This result suggests that the baseline forecast was not a simple statistical estimate.  
It was likely generated using additional business logic or external information that was not included in the dataset used for modeling.

Possible examples include demand smoothing based on long-term historical trends, operational constraints, or internal forecasting rules used in real production systems.  
Because the machine learning models only had access to the limited features available in the dataset, they were unable to replicate the level of refinement embedded in the baseline.

In practice, this means the baseline already represented a well-optimized business forecast rather than a naive benchmark.

## Why Machine Learning Models Did Not Improve Performance

Several machine learning models were tested, including Linear Regression, Random Forest, and LightGBM.  
Despite feature engineering efforts such as lag variables, rolling statistics, and weekly aggregation, the performance improvements were limited.

One key reason was the nature of the dataset itself.  
Most features were operational variables such as inventory level, price, discounts, and calendar information.  
While these features are relevant, they do not fully explain demand behavior on their own.

Feature importance analysis consistently showed that Inventory Level dominated the predictions.  
This indicates that other features provided relatively weak additional signal, making it difficult for the models to significantly reduce prediction error.

Weekly aggregation helped stabilize the data, but it also removed short-term variation that the baseline forecast may already capture more effectively.  
As a result, model complexity alone could not compensate for the lack of richer demand-driving information.

## What This Project Demonstrated

This project demonstrated that stronger models do not automatically lead to better results.

In real-world settings, existing baselines often perform well because they incorporate domain knowledge and historical adjustments that are not explicitly visible in the data.  
Machine learning models are limited by the information they are given, and when that information is incomplete, performance gains are naturally capped.

The most important takeaway from this project is that evaluating and understanding baselines is just as important as building new models.  
Knowing when machine learning adds value and when it does not is a critical skill in applied data analysis.

Rather than viewing the baseline as something that failed to be beaten, this project treated it as a reference point that revealed the limits of the available data and the importance of business context.
