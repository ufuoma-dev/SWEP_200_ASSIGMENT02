# SWEP 200 Assignment 02: Nuclear Heat Exchanger Data Analysis

Data exploration and machine learning on 1,000 operating records from a nuclear plant heat exchanger, prepared ahead of the AI/Machine Learning class.

## Files

| File | Description |
|------|-------------|
| `heat_exchanger_analysis.ipynb` | Jupyter notebook with the full analysis |
| `nuclear_heat_exchanger_1000_data.csv` | Dataset (1,000 rows, 8 columns) |
| `README.md` | This file |

## Dataset

| Column | Meaning |
|--------|---------|
| `Hot_Inlet_Temp_C`, `Hot_Outlet_Temp_C` | Hot-side inlet and outlet temperature (°C) |
| `Cold_Inlet_Temp_C`, `Cold_Outlet_Temp_C` | Cold-side inlet and outlet temperature (°C) |
| `Hot_Mass_Flow_kg_s`, `Cold_Mass_Flow_kg_s` | Hot and cold mass flow rate (kg/s) |
| `Overall_U_W_m2K` | Overall heat transfer coefficient (W/m²K) |
| `Plant_Power_Percent` | Plant power level (%) |

There are no missing values and no duplicate rows.

## What the notebook does

1. Loads and inspects the data
2. Explores distributions, correlations, and relationships with plant power
3. Engineers a Log Mean Temperature Difference (LMTD) feature, assuming counter-flow
4. Trains Linear Regression and Random Forest models to predict `Plant_Power_Percent` (80/20 train/test split)
5. Compares the models and plots feature importance

## Key findings

- Hot inlet temperature, cold inlet temperature, cold outlet temperature, and cold mass flow all rise almost linearly with plant power (correlation about 0.99 to 1.00).
- Hot mass flow and the overall heat transfer coefficient (U) do not change with power.
- Both models predict plant power very accurately on unseen data:

| Model | R² | RMSE | MAE |
|-------|-----|------|-----|
| Linear Regression | 0.9987 | 0.52 | 0.42 |
| Random Forest | 0.9977 | 0.68 | 0.55 |

- Linear Regression slightly outperforms Random Forest because the relationships are close to linear.
- The input variables are strongly correlated with each other, so individual feature importances should be read with care.

## How to run

1. Clone or download this repository
2. Install the requirements: `pip install pandas numpy matplotlib seaborn scikit-learn jupyter`
3. Keep the CSV in the same folder as the notebook
4. Run: `jupyter notebook heat_exchanger_analysis.ipynb`

## Author

**Name:** Ufuoma God'sfavour Ebruphiyor  
**Matric number:** CHE/2023/039  
**Department:** Chemical Engineering, Obafemi Awolowo University
