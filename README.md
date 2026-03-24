# Data Analysis 4 - Assignment 2
## Does Economic Activity Cause CO2 Emissions?

**Author:** Borbála Kovács
**Date:** March 2026

---

## Project Overview

This project investigates the causal relationship between GDP per capita and CO2 emissions per capita using panel data from the World Bank World Development Indicators (WDI), covering 190 countries from 1992 to 2023. We estimate cross-sectional OLS, first-difference, and fixed effects models, and test urbanization as a confounder.

---

## Repository Structure

```
da4_assignment2/
├── code/
│   ├── 01_data_cleaning.ipynb        # Data cleaning & descriptive analysis
│   └── 02_analysis.ipynb             # Regression models & tables
├── data/
│   ├── raw/                          # Original WDI download
│   │   ├── wdi_raw.csv
│   │   └── wdi_series_metadata.csv
│   └── clean/                        # Processed data
│       └── wdi_clean.csv
├── output/                           # Figures and tables
│   ├── fig_distributions.pdf
│   ├── fig_scatter.pdf
│   ├── fig_missing.pdf
│   ├── fig_coverage.pdf
│   ├── tab_main.tex
│   ├── tab_confounder.tex
│   └── tab_sumstats.tex
├── da4_assignment2_report.pdf        # Final report
├── daenv_windows.yml                 # Conda environment file
└── README.md
```

---

## Data Source

World Bank World Development Indicators (WDI):
- **GDP per capita, PPP (constant 2021 $):** `NY.GDP.PCAP.PP.KD`
- **CO2 emissions (Mt, AR5):** `EN.GHG.CO2.MT.CE.AR5`
- **Urban population (% of total):** `SP.URB.TOTL.IN.ZS`
- **Population:** `SP.POP.TOTL`

---

## How to Reproduce

### 1. Environment Setup

```bash
conda env create -f daenv_windows.yml
conda activate daenv
```

Or manually:

```bash
conda create -n daenv python=3.12
conda activate daenv
pip install pandas numpy matplotlib pyfixest
```

### 2. Run the Analysis

Run the notebooks in order:

1. `code/01_data_cleaning.ipynb` — loads raw WDI data, reshapes, cleans, and saves to `data/clean/`
2. `code/02_analysis.ipynb` — estimates all models and exports tables/figures to `output/`

**Approximate run time:** 1–2 minutes total.

---

## Models

| Model | Description |
|-------|-------------|
| OLS 2005 / 2023 | Cross-sectional regressions (two separate years) |
| FD | First difference with year dummies |
| FD + 2 / 6 lags | First difference with lagged GDP growth |
| FE | Country and year fixed effects |

All panel models use clustered standard errors at the country level.

---

## AI Usage Disclosure

AI (Claude) was used for:
- Code generation and debugging
- Report drafting and formatting

All outputs were verified and validated by the author.
