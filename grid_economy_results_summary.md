# Grid Economy Analysis Results

This document captures the verified output from the synthetic duck-curve and market-price analysis run in the project workspace.

## Verification run

Command used:

```powershell
cd "c:\Users\Dell\OneDrive\Grid Economy"; .\.venv\Scripts\python.exe "c:/Users/Dell/OneDrive/Grid Economy/grid_economy_analysis.py"
```

Status: completed successfully with exit code 0.

## Key findings

### 1) Merit-order effect regression

- Estimated renewable penetration coefficient: beta_RE = -0.054785
- Estimated ramp-rate coefficient: beta_Ramp = 0.002807

Interpretation:
- A negative beta_RE indicates that higher renewable penetration depresses market clearing price (MCP) because zero-marginal-cost renewable generation displaces thermal generation.
- A positive beta_Ramp indicates that rapid increases in net load force expensive peaking generation and raise MCP.

### 2) Granger causality test

Granger test for ramp rate -> MCP:
- Lag 1: p-value = 0.00000 -> statistically significant
- Lag 2: p-value = 0.00000 -> statistically significant
- Lag 3: p-value = 0.00000 -> statistically significant
- Lag 4: p-value = 0.00000 -> statistically significant

Interpretation:
- Ramp-rate dynamics strongly predict MCP changes, consistent with evening peak and duck-curve stress conditions.

### 3) SARIMAX evening forecast

Forecast metrics:
- RMSE: ₹1.7763 / kWh
- MAE: ₹1.4419 / kWh
- MAPE: 12.60%

Evening window evaluation (17:00-22:00):
- Evening RMSE: ₹1.3842 / kWh
- Evening MAE: ₹1.1169 / kWh

## Generated output files

- [duck_curve_synthetic.png](duck_curve_synthetic.png)
- [mcp_vs_net_load.png](mcp_vs_net_load.png)
- [sarimax_evening_forecast.png](sarimax_evening_forecast.png)

## Summary

The synthetic duck-curve model, econometric regression, Granger causality checks, and exogenous-driver SARIMAX forecast all completed successfully and produced consistent results aligned with the expected market behavior.
