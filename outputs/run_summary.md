# Hospital OPD Time Series Analysis — Run Summary
- Data rows after cleaning: 52343
- Daily observations: 365
- Date range: 2024-04-19 to 2025-04-18
- Departments: Cardiology, Dermatology, General Medicine, Neurology, Orthopedics, Pediatrics
- Forecast horizon: 30 days

## Best classical/VAR model by RMSE
- Cardiology: AR_7 | MAE=3.521 | RMSE=4.292 | MAPE=15.983%
- Dermatology: Naive | MAE=3.205 | RMSE=4.187 | MAPE=13.726%
- General Medicine: ARMA_2_2 | MAE=2.837 | RMSE=3.443 | MAPE=12.347%
- Neurology: AR_7 | MAE=3.215 | RMSE=3.994 | MAPE=13.987%
- Orthopedics: Naive | MAE=3.151 | RMSE=3.697 | MAPE=13.847%
- Pediatrics: ARMA_2_2 | MAE=3.172 | RMSE=3.903 | MAPE=14.361%
- TOTAL: ARMA_2_2 | MAE=7.636 | RMSE=9.691 | MAPE=5.363%