Renewable Energy Output Prediction Using XGBoost and LightGBM
This project predicts solar power generation using weather and time-related features.
Dataset
Recommended Kaggle dataset:
Solar Power Generation Data  
https://www.kaggle.com/datasets/anikannal/solar-power-generation-data
Place the downloaded CSV files in:
```text
dataset/raw/
```
Expected files:
```text
Plant_1_Generation_Data.csv
Plant_1_Weather_Sensor_Data.csv
Plant_2_Generation_Data.csv
Plant_2_Weather_Sensor_Data.csv
```
Plant 2 is optional. The code works with Plant 1 alone.
Project Structure
```text
Renewable_Energy_Complete_Project/
│
├── dataset/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── 01_EDA.ipynb
│   ├── 02_Preprocessing.ipynb
│   ├── 03_Feature_Engineering.ipynb
│   ├── 04_XGBoost_Model.ipynb
│   ├── 05_LightGBM_Model.ipynb
│   └── 06_Model_Comparison.ipynb
│
├── src/
│   ├── __init__.py
│   ├── preprocessing.py
│   ├── feature_engineering.py
│   ├── xgboost_model.py
│   ├── lightgbm_model.py
│   └── evaluation.py
│
├── models/
├── results/
├── app/
│   └── app.py
│
├── main.py
├── requirements.txt
└── README.md
```
Features Used
The model uses:
AMBIENT_TEMPERATURE
MODULE_TEMPERATURE
IRRADIATION
HOUR
MINUTE
DAY
MONTH
DAY_OF_WEEK
HOUR_SIN
HOUR_COS
Target:
```text
AC_POWER
```
Why DC_POWER is not used as an input
DC_POWER is closely related to AC_POWER and using it can create target leakage.
The project therefore predicts AC_POWER only from weather and time features.
Install
Open terminal inside the project folder:
```bash
pip install -r requirements.txt
```
Run the ML project
```bash
python main.py
```
After execution, the project automatically creates:
Processed Data
```text
dataset/processed/solar_power_processed.csv
```
Result Files
```text
results/
├── 01_power_over_time.png
├── 02_irradiation_vs_power.png
├── 03_temperature_vs_power.png
├── 04_correlation_heatmap.png
├── 05_actual_vs_predicted.png
├── 06_xgboost_feature_importance.png
├── 06_xgboost_feature_importance.csv
├── 07_lightgbm_feature_importance.png
├── 07_lightgbm_feature_importance.csv
├── comparison_mae.png
├── comparison_rmse.png
├── comparison_r2.png
├── comparison_training_time_seconds.png
├── model_metrics.csv
└── predictions.csv
```
Trained Models
```text
models/
├── xgboost_model.pkl
├── lightgbm_model.pkl
└── feature_columns.pkl
```
Run Streamlit App
First run:
```bash
python main.py
```
Then:
```bash
streamlit run app/app.py
```
Evaluation Metrics
The models are evaluated using:
MAE
RMSE
R² Score
Training Time
Lower MAE and RMSE are better.
Higher R² is better.
