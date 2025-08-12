# AOX Trade - Polish Electricity Market Analysis

## Overview

This project analyzes the relationship between key commodities and power prices within the Polish electricity market. As a power trader, the goal is to develop various forecasts to inform trading strategies for the upcoming week.

## Background

The Polish power market is predominantly fueled by coal and gas-fired power plants, with a rapidly increasing share of renewable energy sources. Recent geopolitical events, including the war in Ukraine, have led to heightened volatility in natural gas prices, significantly impacting electricity prices across Europe.

## Dataset

The analysis uses a comprehensive dataset for Poland, which includes:

1. **Historical day-ahead power prices** in hourly resolution
2. **Commodity prices** of natural gas, hard coal, and CO2 allowances
3. **Hourly generation data** by fuel type
4. **Hourly import/export positions**
5. **Total installed capacity** of solar and wind power plants

## Project Structure

```
aoxtrade/
├── original_data/
│   ├── Case Study Data .xlsx    # Raw Excel data with multiple sheets
│   ├── Case Study.pdf           # Case study requirements and context
│   ├── clean_data.csv          # Processed and merged dataset
│   └── preprocess_data.ipynb   # Data preprocessing notebook
├── task1.ipynb                 # Main analysis notebook
└── README.md                   # This file
```

## Analysis Tasks

### 1. Commodity-Price Relationship Analysis
- Model and quantify the influence of natural gas, coal, and CO2 allowance prices on day-ahead electricity prices
- Suggest potential trading strategies based on findings

### 2. Power Price Evolution Analysis
- Visualize the evolution of day-ahead power prices over time
- Quantify trends and provide explanations (seasonality, geopolitical factors)
- Derive non-trivial observations to inform trading decisions

### 3. Load Profile Analysis
- Analyze Polish electricity load profile patterns and their evolution
- Visualize typical weekday and weekend load profiles
- Identify distinct patterns and changes over time

### 4. Price Forecasting
Forecast average day-ahead prices for the period **13.06.2024 - 19.06.2024** given the following conditions:

- **Solar output**: Expected to increase by 10% compared to the previous week (06.06.2024-12.06.2024)
- **Wind capacity**: New 300MW turbine coming online on 13.06.2024 with 70% capacity factor (210MW)
- **Cold surge**: One night during the period will see 15% increase in power demand (00-06 hours)
- **Other factors**: Remain unchanged from the previous week

## Data Processing

The project includes a comprehensive data preprocessing pipeline:

- **Upsampling**: Converts daily/monthly data to hourly frequency
- **Data cleaning**: Handles missing values, standardizes column names
- **Merging**: Combines multiple data sources into a unified dataset
- **Visualization**: Generates histograms and time series plots for analysis

## Key Variables

### Generation Mix
- Biomass, Brown coal/lignite, Coal derived gas
- Natural gas, Hard coal, Oil
- Hydro (pumped storage, run-of-river, water reservoir)
- Solar, Wind

### Price Variables
- Day-ahead electricity prices (EUR/MWh)
- Natural gas prices (EUR/MWh)
- CO2 allowance prices (EUR/ton)
- Coal prices (EUR/ton)

### Market Data
- Load/demand
- Import/export positions
- Trade balance
- Installed renewable capacity

## Technical Implementation

- **Python 3.9+** with conda environment management
- **Key libraries**: pandas, numpy, matplotlib, seaborn, scikit-learn
- **Data format**: Excel input → CSV output with hourly timestamps
- **Visualization**: Automated plotting for different variable groups

## Getting Started

### Environment Setup
```bash
# Create and activate conda environment
conda create -n aoxtrade python=3.10
conda activate aoxtrade

# Install required packages
conda install -c conda-forge pandas numpy matplotlib seaborn scikit-learn
```

### Running the Analysis
```bash
# Run preprocessing
python preprocess.py

# Or use Jupyter notebooks
jupyter notebook task1.ipynb
```

## Expected Outcomes

1. **Statistical models** quantifying commodity-price relationships
2. **Trading strategy recommendations** based on identified patterns
3. **Price forecasts** for the specified week with confidence intervals
4. **Risk assessment** considering various market factors
5. **Actionable insights** for power trading decisions

## Market Context

This analysis is particularly relevant given:
- **Energy transition** towards renewable sources
- **Geopolitical instability** affecting gas supplies
- **Carbon pricing** mechanisms (EU ETS)
- **Market liberalization** in European electricity markets
- **Seasonal patterns** in both demand and renewable generation

## Contributing

This is a case study project for power trading analysis. The methodology and findings can be extended to other electricity markets or adapted for different time periods.

## License

This project is for educational and analytical purposes related to energy market analysis.
