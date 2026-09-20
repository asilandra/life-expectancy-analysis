# Socioeconomic Determinants of Life Expectancy: A Cross-Sectional Analysis

A statistical analysis examining the relationship between GDP per capita, health 
expenditure, adult mortality, and income-group classification on life expectancy 
at birth, using World Bank data for 191 countries (2018).

## Overview

This project tests two hypotheses:

- **H1:** Life expectancy is significantly associated with log-transformed GDP per 
  capita, health expenditure (% of GDP), and adult mortality rate, after controlling 
  for income-group classification.
- **H2:** Mean life expectancy differs significantly across the World Bank's four 
  income-group classifications (Low, Lower-middle, Upper-middle, High income).

## Data Source

World Bank [World Development Indicators (WDI)](https://databank.worldbank.org/source/world-development-indicators), 
accessed via the official [`wbgapi`](https://pypi.org/project/wbgapi/) Python package.

## Methods

- **Multiple linear regression** (OLS), refitted with heteroscedasticity-consistent 
  (HC3) robust standard errors after residual diagnostics identified 
  heteroscedasticity.
- **Model validation:** 80/20 train/test split and 10-fold cross-validation.
- **Influence diagnostics:** Cook's Distance, with a sensitivity analysis excluding 
  influential observations.
- **One-way ANOVA** with Tukey HSD post-hoc comparisons for the income-group 
  hypothesis.
- **Multicollinearity checks:** Variance Inflation Factor (VIF), applied both before 
  and after combining correlated predictors.

## Key Findings

- GDP per capita (log-transformed), health expenditure, and adult mortality rate are 
  all significant, independent predictors of life expectancy (R² = 0.960).
- Life expectancy differs significantly across every pairwise income-group 
  comparison (η² = 0.648).
- Under heteroscedasticity-robust inference, the Lower-middle-income group does not 
  differ significantly from the Low-income reference — a nuance masked by standard 
  (non-robust) inference.
- Sensitivity analysis confirms the results are not driven by a small number of 
  influential countries, though the GDP effect's magnitude is moderately sensitive 
  to a subset of countries with atypical mortality-to-income profiles (e.g. Lesotho, 
  Eswatini).

## Repository Structure

├── kv6015_analysis_clean.ipynb # Full analysis pipeline (13 sequential scripts)
├── outputs/ # Result charts and processed data
└── README.md


## Tools

Python — `pandas`, `numpy`, `statsmodels`, `scipy`, `scikit-learn`, `seaborn`, 
`matplotlib`, `wbgapi`

## License

Code in this repository is released under the MIT License (see `LICENSE`).

Data sourced from the World Bank's World Development Indicators, released under 
[CC BY 4.0](https://datacatalog.worldbank.org/public-licenses#cc-by).
## Notes

Developed and executed in a Kaggle Notebook environment.
