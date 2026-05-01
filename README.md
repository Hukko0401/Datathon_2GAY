# Datathon_2GAY
# Revenue Forecasting - Datathon

> Dự báo doanh thu và COGS cho một công ty thương mại điện tử dựa trên dữ liệu lịch sử 10 năm (2012-2022)

## Overview

Dự án này thực hiện dự báo doanh thu (`Revenue`) và giá vốn hàng bán (`COGS`) theo ngày cho giai đoạn **2023-01-01 đến 2024-07-01** (548 ngày). Dữ liệu bao gồm 14 bảng liên quan đến orders, customers, products, promotions, web traffic, inventory.

**Best Score:** RMSE ~917,000
2. Cài đặt thư viện
bash
pip install -r requirements.txt
3. Chạy notebook
Mở và chạy revenue_forecasting_v2.ipynb theo thứ tự các cells.

Results
Model Performance (Validation 2022)
Model	RMSE	MAE	R²
Linear Regression	~1,800,000	~1,200,000	0.45
Random Forest	~1,200,000	~850,000	0.65
XGBoost (baseline)	1,183,334	852,045	0.774
XGBoost (tuned)	815,009	570,159	0.7563
LightGBM (tuned)	821,271	577,407	0.7525
Ensemble (XGB+LGB)	814,290	569,364	0.7567
Top 10 Features
Feature	Importance
lag_1	0.22
lag_365	0.10
rolling_min_7	0.10
rolling_median_7	0.06
cos_quarter	0.03
lag_730	0.03
rolling_median_30	0.02
rolling_mean_7	0.02
traffic_conversion	0.02
rolling_max_7	0.02
Key Techniques
Kỹ thuật	Mô tả
Walk-forward CV	Time-series cross-validation (5 folds, gap=7)
Fourier features	sin/cos encoding cho mùa vụ (năm, tuần, quý)
Feature engineering	70+ features (lags, rolling, holiday, traffic, promo)
Hyperparameter tuning	Optuna Bayesian optimization (80 trials)
Ensemble	Weighted average XGBoost + LightGBM
Timeline
Phase	Thời gian
EDA & Preprocessing	2 ngày
Feature Engineering	3 ngày
Model Development	2 ngày
Hyperparameter Tuning	2 ngày
Optimization	2 ngày


Best Score: RMSE 917,000

