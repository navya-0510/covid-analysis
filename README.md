# COVID-19 Data Analysis

End-to-end data analysis pipeline on the Our World in Data COVID-19 dataset, built in Python (Google Colab).

## Overview
This project performs in-depth analysis of global COVID-19 trends across 8 countries — India, United States, Brazil, United Kingdom, Germany, South Africa, Japan, and Australia — covering the full pandemic period from 2020 to 2024.

## What this project covers

### Data pipeline
- Loaded and cleaned the OWID COVID-19 dataset (395,000+ rows, 237 countries)
- Filtered aggregate rows using continent-based validation
- Forward-filled cumulative columns per country, clipped negative corrections
- Computed 7-day rolling averages to smooth weekend reporting gaps
- Merged World Bank GDP data (2019 baseline) for economic analysis

### Exploratory data analysis
- Per-country summary table: total cases, deaths, CFR, cases per million
- Correlation heatmap: COVID outcomes vs GDP, HDI, vaccination rate, median age, hospital beds

### Wave detection
- Algorithmically detected COVID waves using `scipy.signal.find_peaks`
- Tuned prominence and minimum distance parameters to avoid noise spikes
- Visualised wave peaks across all 8 focus countries

### Forecasting
- Trained Facebook Prophet models per country on 7-day rolling case averages
- Generated 30-day ahead forecasts with 95% confidence intervals
- Exported forecast data for all 8 countries

### Statistical analysis
- Linear regression: vaccination rate vs case fatality rate (R², p-value)
- Full Pearson correlation table across all metric pairs with significance levels
- Welch t-test comparing CFR between high and low vaccination country groups

## Key findings
- Vaccination rate shows a statistically significant negative correlation with CFR (r = -0.37)
- Countries with ≥50% vaccination coverage had meaningfully lower case fatality rates
- Wave detection identified distinct pandemic waves across all focus countries
- HDI and GDP per capita are strongly correlated with vaccination coverage (r = 0.55, 0.50)

## Outputs
| File | Description |
|------|-------------|
| `outputs/correlation_heatmap.png` | Heatmap of COVID outcomes vs country factors |
| `outputs/wave_detection.png` | Detected wave peaks across 8 countries |
| `outputs/regression_vacc_cfr.png` | Vaccination rate vs CFR regression scatter |
| `outputs/wave_dates.csv` | Algorithmically detected wave peak dates |
| `outputs/covid_forecasts.csv` | 30-day Prophet forecasts per country |
| `outputs/country_summary.csv` | Per-country metrics summary table |

## How to run
1. Open `covid19_data_visualisation_dashboard.ipynb` in Google Colab
2. Download the datasets:
   - [OWID COVID-19 data](https://covid.ourworldindata.org/data/owid-covid-data.csv)
   - [World Bank GDP](https://data.worldbank.org/indicator/NY.GDP.MKTP.CD) → Download → CSV
3. Upload both files when prompted in the notebook
4. Run all cells in order

> Raw dataset files are not included in this repo due to size (80MB+). Download from the links above.

## Stack
`Python` `pandas` `numpy` `matplotlib` `seaborn` `scipy` `Prophet` `Plotly` `Google Colab`
