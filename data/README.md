# Data

Raw data files are not included in this repository (third-party license restrictions).

## Price, volume and risk-free rate

Downloaded automatically via `yfinance` the first time you run the notebook. The files `prices.csv`, `volume.csv` and `rf_irx.csv` are saved in this folder.

## ESG scores (manual download)

1. Download the "S&P 500 ESG Risk Ratings" dataset from Kaggle: https://doi.org/10.34740/kaggle/ds/3660201
2. Save it in this folder as `esg_kaggle.csv`.

The notebook reads two columns from this file:

- `Symbol`
- `Total ESG Risk score` (Sustainalytics rating, lower means less risk)

The scores are a snapshot from December 2022 - January 2023. Stocks without a score are excluded from the ESG strategies.

## Sectors (optional)

If you add a `sectors.csv` file (ticker as index, one column named `Sector`), sector labels are added to the output tables. The notebook runs without it.

## Expected folder layout

```
data/
├── esg_kaggle.csv    (add manually)
├── prices.csv        (created automatically)
├── volume.csv        (created automatically)
└── rf_irx.csv        (created automatically)
```
