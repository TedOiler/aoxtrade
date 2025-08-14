# AOX Trade - Polish Electricity Market Analysis

## Overview

This repository contains my solution to the AOX Trade company interview case study, which focuses on analyzing the relationship between key commodities and power prices within the Polish electricity market. As a power trader, the goal is to develop various forecasts to inform trading strategies for the upcoming week.

## Background

The Polish power market is predominantly fueled by coal and gas-fired power plants, with a rapidly increasing share of renewable energy sources. Recent geopolitical events, including the war in Ukraine, have led to heightened volatility in natural gas prices, significantly impacting electricity prices across Europe.

## Dataset

The analysis uses a comprehensive dataset for Poland, which includes:

1. **Historical day-ahead power prices** in hourly resolution
2. **Commodity prices** of natural gas, hard coal, and CO2 allowances
3. **Hourly generation data** by fuel type
4. **Hourly import/export positions**
5. **Total installed capacity** of solar and wind power plants

## Repository Structure

```
aoxtrade/
├── original_data/
│   ├── Case Study Data .xlsx    # Raw Excel data with multiple sheets
│   ├── Case Study.pdf           # Case study requirements and context
│   ├── clean_data.csv          # Processed and merged dataset
│   └── preprocess.ipynb        # Data preprocessing notebook
├── task1/                      # Task 1: Commodity-Price Relationship Analysis
│   ├── task1.ipynb            # Main analysis notebook
│   ├── skfda_hour_betas.csv   # Hourly beta coefficients
│   ├── skfda_month_betas.csv  # Monthly beta coefficients
│   ├── skfda_quarter_betas.csv # Quarterly beta coefficients
│   └── [additional outputs]   # Various analysis results
├── task2/                      # Task 2: Power Price Evolution Analysis
│   ├── task2.ipynb            # Main analysis notebook
│   ├── arima_auto_metrics.csv # ARIMA model metrics
│   ├── day_of_week_avg.csv    # Day-of-week averages
│   ├── intraday_hourly_mean.csv # Intraday hourly means
│   └── [additional outputs]   # Various analysis results
├── task3/                      # Task 3: Load Profile Analysis
│   ├── task3.ipynb            # Main analysis notebook
│   ├── industrial_hourly_excess_shape.csv # Load shape analysis
│   ├── hourly_load_by_year_wd_we.png # Load visualization
│   └── [additional outputs]   # Various analysis results
├── task4/                      # Task 4: Price Forecasting
│   ├── task4.ipynb            # Main analysis notebook
│   ├── actual_vs_prediction.png # Forecast vs actual comparison
│   ├── coefficients_alpha_beta.png # Model coefficients
│   ├── actual_daily.csv       # Actual daily prices
│   ├── predictions_daily.csv  # Daily price predictions
│   └── [additional outputs]   # Various analysis results
├── final_report/               # Final report (to be added)
├── requirements.txt            # Python dependencies
└── README.md                   # This file
```

## Analysis Tasks

### Task 1: Commodity-Price Relationship Analysis
**Location**: `task1/task1.ipynb`

**Objective**: Model and quantify the influence of natural gas, coal, and CO2 allowance prices on day-ahead electricity prices, and suggest potential trading strategies based on findings.

**Key Outputs**:
- Functional data analysis using scikit-fda
- Hourly, monthly, and quarterly beta coefficients
- Trading strategy recommendations

### Task 2: Power Price Evolution Analysis
**Location**: `task2/task2.ipynb`

**Objective**: Visualize the evolution of day-ahead power prices over time, quantify trends, and provide explanations (seasonality, geopolitical factors). Derive non-trivial observations to inform trading decisions.

**Key Outputs**:
- Time series decomposition (STL)
- ARIMA modeling and auto-selection
- Seasonal and trend analysis
- Day-of-week and intraday patterns

### Task 3: Load Profile Analysis
**Location**: `task3/task3.ipynb`

**Objective**: Develop a detailed analysis of the Polish electricity load profile by identifying distinct patterns and how they have changed throughout time. Visualize typical weekday and weekend load profiles.

**Key Outputs**:
- Load profile visualizations
- Weekday vs weekend patterns
- Temporal evolution analysis
- Industrial load shape analysis

### Task 4: Price Forecasting
**Location**: `task4/task4.ipynb`

**Objective**: Forecast average day-ahead prices for the period **13.06.2024 - 19.06.2024** given specific market conditions.

**Forecasting Scenario**:
- **Solar output**: Expected to increase by 10% compared to the previous week (06.06.2024-12.06.2024)
- **Wind capacity**: New 300MW turbine coming online on 13.06.2024 with 70% capacity factor (210MW)
- **Cold surge**: One night during the period will see 15% increase in power demand (00-06 hours)
- **Other factors**: Remain unchanged from the previous week

**Key Outputs**:
- Functional linear regression model
- Alpha and beta coefficient curves
- Daily price predictions
- Actual vs prediction comparison

## Data Processing

The project includes a comprehensive data preprocessing pipeline in `original_data/preprocess.ipynb`:

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

- **Python 3.9+** with virtual environment management
- **Key libraries**: pandas, numpy, matplotlib, seaborn, scikit-fda, statsmodels, pmdarima
- **Data format**: Excel input → CSV output with hourly timestamps
- **Visualization**: Automated plotting for different variable groups
- **Functional Data Analysis**: Advanced statistical modeling using scikit-fda

## Getting Started

### Environment Setup
```bash
# Create and activate virtual environment
python -m venv aoxtrade
source aoxtrade/bin/activate  # On Windows: aoxtrade\Scripts\activate

# Install required packages
pip install -r requirements.txt
```

### Running the Analysis
```bash
# Start with data preprocessing
jupyter notebook original_data/preprocess.ipynb

# Then run tasks in order
jupyter notebook task1/task1.ipynb
jupyter notebook task2/task2.ipynb
jupyter notebook task3/task3.ipynb
jupyter notebook task4/task4.ipynb
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
