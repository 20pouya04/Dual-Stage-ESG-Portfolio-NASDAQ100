# Dual-Stage ESG-Aligned Portfolio Construction (NASDAQ-100)

A two-stage portfolio construction framework for the NASDAQ-100 that combines machine-learning-based stock preselection with ESG-aware portfolio optimization, built in Python.

The system first uses a **Random Forest** model to rank NASDAQ-100 stocks by their predicted probability of beating the QQQ benchmark, then builds a **minimum-variance portfolio** from the top-ranked stocks, optionally constrained to keep the portfolio's ESG risk score below a chosen cap. Performance is evaluated with a quarterly walk-forward backtest against QQQ, equal-weighting, and a few other simple baselines.

This code accompanies a research manuscript:

> P. Ahadpour Bakhtiari, H. Ghanbari, R. R. Kumar, & P. J. Stauvermann, *"A Dual-Stage Framework for Sustainable Portfolio Construction: Leveraging Machine Learning-Based Asset Preselection and ESG-Aligned Mean-Variance Optimization"* (manuscript under review).

## Methodology

1. **Preselection (Stage 1):** NASDAQ-100 stocks are filtered by volatility and trading volume, then ranked each quarter by a Random Forest trained on past price/volume features to predict which stocks will outperform QQQ.
2. **Optimization (Stage 2):** A minimum-variance portfolio is built from the top-ranked stocks (Ledoit-Wolf covariance, 10% max weight per stock), optionally with a cap on the portfolio's ESG risk score.
3. **Backtest:** The whole pipeline is re-run every quarter from 2020 to 2026 and compared against QQQ, equal-weighting, and momentum-based selection.

## Repository Contents

| File | Description |
|---|---|
| `Compact_Analysis.ipynb` | Full pipeline: data loading, Random Forest preselection, portfolio optimization, backtest, and figures |
| `data/README.md` | Where to get the price and ESG data |
| `requirements.txt` | Python package requirements |
| `LICENSE` | MIT License |

## Requirements

- Python >= 3.10
- Packages listed in `requirements.txt`

```bash
pip install -r requirements.txt
```

## How to Run

1. Add `esg_kaggle.csv` to the `data/` folder (see `data/README.md`).
2. Open `Compact_Analysis.ipynb` and run all cells.
3. Price and volume data are downloaded automatically on first run. Results and figures are saved to an `out/` folder.

## Author

**Pouya Ahadpour Bakhtiari**
School of Industrial Engineering, Islamic Azad University, West Tehran Branch
[ORCID: 0009-0008-8523-8451](https://orcid.org/0009-0008-8523-8451)

## License

MIT License - see [LICENSE](./LICENSE).
