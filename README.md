# Crime Data Analysis
# Los Angeles Crime Data Analysis (2020-Present)
A comprehensive data analytics project analyzing crime patterns in Los Angeles using over one million incident reports from the Los Angeles Police Department (LAPD). This project applies advanced data cleaning, exploratory data analysis, and predictive modeling techniques to uncover actionable insights for law enforcement and public safety initiatives.

## Project Overview
This analysis examines crime patterns in Los Angeles from January 1, 2020, to May 29, 2025, covering a critical period that encompasses the COVID-19 pandemic, social justice movements, and subsequent recovery phases. The project demonstrates the practical application of data science techniques to real-world public safety challenges, providing evidence-based insights for strategic resource allocation and crime prevention.

## Key Findings
- Crime Trends: Peak crime occurred in 2022 with 235,259 incidents (17.7% increase from 2020), stabilizing in 2023
- COVID-19 Impact: Initial lockdown (March 2020) resulted in 13.5% decrease in daily crime rates; full reopening (June 2021) corresponded with 9.3% increase
- Dominant Crime Type: Vehicle theft leads with 115,190 incidents (11.46% of all crimes) and is the only major crime type showing an increasing trend
- Geographic Disparities: Central division experiences twice the crime volume of Foothill division (110% disparity)
- Temporal Patterns: Friday afternoons at noon represent peak crime periods; weekdays account for 71.4% of all crimes
- Victim Demographics: Adults aged 31-45 represent 25.55% of victims; males experience 13% higher victimization rates

## Dataset
- Source: Los Angeles Open Data Portal
- Dataset: Crime Data from 2020 to Present
- Records: 1,004,991 crime incidents
- Timeframe: January 1, 2020 - May 29, 2025
- Update Frequency: Weekly
- Original Columns: 28
- Final Columns: 39 (after feature engineering)

## Methodology
### 1. Data Cleaning & Preparation
Operations Performed:

- Column standardization to snake_case format (28 columns)
- Duplicate removal (0 duplicates confirmed)
- Date/time conversion (100% success rate across 1,004,991 records)
- Missing value imputation (144,644 gender, 144,656 descent records)
- Outlier correction (137 age outliers replaced with median)
- Categorical standardization across all text fields
- Feature engineering (11 new temporal and derived features)

### 2. Exploratory Data Analysis (EDA)
Statistical Analysis:

- Yearly distribution and trends (2020-2025)
- Geographic distribution across 21 LAPD areas
- Temporal patterns (hourly, daily, weekly, monthly, seasonal)
- Crime type frequency analysis (140+ categories)
- Victim demographic profiling (age, gender, descent)

#### Key Metrics:

- Mean crime count per LAPD area: 47,857 (σ = 8,765)
- Victim age: mean 28.9 years, median 30 years
- Weekday-to-weekend ratio: 2.5:1

### 3. Advanced Predictive Modeling
Three modeling approaches implemented:
#### Regression Models (Weekly Aggregation)

- Linear Regression: R² = -3.76
- Polynomial Regression (degree 2): R² = -9.42
- Evaluation: MAE, RMSE
- Forecast: 12-week forward predictions

#### ARIMA Time Series (Monthly Aggregation)

- Model: ARIMA(1,1,1)
- Performance: MAE = 486.90 crimes/month (2.7% error)
- Stationarity test: Augmented Dickey-Fuller (p = 0.6844)
- Forecast: 6-month forward predictions

#### Random Forest Classification

- Dataset: Top 5 crime types (377,175 records)
- Features: Hour, Day_of_Week, Month, Is_Weekend, Area_Code, Victim_Age, Quarter
- Split: 80-20 stratified (301,740 training, 75,435 test)
- Configuration: 100 estimators, max_depth=10
- Performance: 57.15% overall accuracy, 99.61% for vehicle theft
- Feature Importance: Victim age (87.7%), Hour (7.8%), Area code (3.2%)
