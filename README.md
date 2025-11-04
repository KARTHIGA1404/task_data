[🚀 Launch data.ipynb in Binder](https://mybinder.org/v2/gh/KARTHIGA1404/task_data/0aa9f14d4e828aee7e9a289ac7465b4c3ab3058f?filepath=data.ipynb)

<img width="1697" height="366" alt="image" src="https://github.com/user-attachments/assets/dcf55a80-ed08-422c-940a-1a67ff0b9938" />
## Key Analytical Insights
Weekly and seasonal patterns are prominent — weekday ridership peaks while weekends show noticeable declines.
Local Route and Peak Service exhibit higher variability, reflecting commuter-driven travel demand.
Light Rail and School routes are relatively stable, where ARIMA performed better due to smoother data behavior.
Outliers linked to holidays or events were removed and interpolated, leading to improved forecast stability.
The average MAPE across all transport modes is below 10%, indicating strong predictive reliability and consistent model performance.
## Operational Insights
Accurate 7-day forecasts enable data-driven decisions in fleet and staff allocation.
Predicting peak periods helps prevent overcrowding and improve service efficiency.
Seasonal demand planning ensures optimal utilization of resources across routes.
The model can be integrated into a transport management dashboard for real-time forecasting updates.


# Forecasting Transport Usage using Prophet–ARIMA Hybrid Model

## Objective
To develop an accurate short-term forecasting model for transport usage trends across multiple routes using a hybrid ensemble of Facebook Prophet and ARIMA, ensuring predictive stability with MAPE < 10%.

## Algorithm Overview
The Prophet model captures complex trend, seasonality, and holiday effects, ideal for non-stationary series.  
ARIMA (AutoRegressive Integrated Moving Average) models linear time dependencies through differencing and lag relationships, performing well on smoother data.  
Combining both leverages Prophet’s flexibility and ARIMA’s precision.

## Model Parameters

### Prophet
- yearly_seasonality=True, weekly_seasonality=True, daily_seasonality=True — captures periodic patterns  
- changepoint_prior_scale=0.02 — controls trend smoothness  
- seasonality_prior_scale=15.0 — adjusts seasonality strength  
- interval_width=0.90 — 90% prediction confidence interval  
- add_country_holidays('US') — includes holiday impacts  

### ARIMA (2,1,2)
- p=2 → autoregressive terms  
- d=1 → first differencing for stationarity  
- q=2 → moving average terms  

## Evaluation Metrics
- MAE (Mean Absolute Error) – average prediction deviation  
- RMSE (Root Mean Squared Error) – penalizes large errors  
- MAPE (Mean Absolute Percentage Error) – primary measure for forecast accuracy  

## Hybrid Ensemble Formula
Final Forecast = 0.7 × Prophet + 0.3 × ARIMA  

This weighted ensemble balances Prophet’s nonlinear adaptability with ARIMA’s linear stability.

## Results & Key Insights
- Achieved MAPE < 10% for all transport modes  
- Prophet performed best for variable routes (Local, Peak Service); ARIMA excelled on steady series (Light Rail, School)  
- Weekly and seasonal ridership trends detected — weekday peaks, weekend drops  
- Data cleaning and outlier removal significantly improved forecast consistency  

## Conclusion
The Prophet–ARIMA hybrid model provides highly reliable, interpretable forecasts for transport operations.  
It supports data-driven planning, fleet management, and peak-time optimization.  
The model’s strong performance and scalability make it ideal for integration into real-time analytics platforms at Kovai.co.
