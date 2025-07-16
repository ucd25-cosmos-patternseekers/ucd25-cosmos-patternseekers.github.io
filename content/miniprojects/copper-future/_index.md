## Model Performance

| Metric | Value |
|--------|-------|
| Training MAE | $0.0300 |
| Test MAE | $0.0543 |
| Test R² | 0.9394 |
| Error as % of Price | 1.35% |

## Feature Importance

| Feature | Importance |
|---------|------------|
| price_lag_1 | 0.540529 |
| price_lag_2 | 0.328109 |
| ma_5 | 0.126359 |
| price_lag_3 | 0.001779 |
| diff_from_ma5 | 0.001672 |
| price_lag_5 | 0.000710 |
| ma_20 | 0.000401 |
| spread | 0.000228 |
| volatility | 0.000212 |

![](prediction.png)