# VIX Pair Trading

This repository contains the implementation of a volatility pair trading strategy between Nifty and Bank Nifty indices. The project focuses on capturing volatility dispersion between these two highly correlated indices using their implied volatilities.

## Project Overview

The research thesis explores the relationship between Nifty and Bank Nifty indices, which have significant overlap in their constituents and weights. The strategy aims to capitalize on the dispersion in their volatilities, which are influenced by similar market conditions and macroeconomic factors.

### Data Description
- Minute-level implied volatilities (IVs) of Bank Nifty and Nifty
- Time To Expiry (TTE) for each data point
- Trading hours: 09:15 to 15:30 (Indian market hours)

## Data Processing Pipeline

### 1. Initial Data Cleaning (`Cleaning_data.ipynb`)

- **Trading Hours Filtering**: Retained only market hours data (9:15 AM – 3:30 PM)
- **Missing Value Treatment**: 
  - Implemented weighted average interpolation for missing values
  - Used ±5-minute window with dynamic expansion up to ±10 minutes
  - Applied higher weights to closer timestamps for more accurate interpolation
- **TTE Anomaly Detection**:
  - Identified and corrected inconsistent Time-To-Expiry values
  - Used mode-based correction for each trading day

### 2. Data Preprocessing (`preprocessing_data.ipynb`)

- **Abnormal Pattern Detection**:
  - Implemented 3-point rolling slope analysis
  - Detected and flagged segments with artificial/suspicious patterns
  - Identified exact slope segments indicating potential data issues
- **Data Validation**:
  - Created visualization tools to highlight:
    - Normal data segments
    - Invalid/suspicious patterns
    - Missing data gaps
  - Generated filtered dataset with only valid data points

### 3. Data Quality Improvements

- Original dataset was refined to create `valid_market_df.xlsx`
- Removed artificial patterns and suspicious data points
- Ensured data quality for subsequent modeling phases

## Project Status

🚧 **Work in Progress**

Currently completed:
- Data cleaning and preprocessing
- Data quality validation
- Initial exploratory analysis

Next steps:
- Implementation of z-score based trading system
- Development of enhanced trading model
- Performance comparison and optimization

## Formulae Used

```
Spread = Bank Nifty IV - Nifty IV
P/L = Spread × (Time To Expiry)^0.7
```

## Dependencies

- Python 3.x
- pandas
- numpy
- matplotlib

## Contact

For any queries regarding this project, please feel free to reach out.