# API Data Collector

A Python tool that pulls live weather forecast data from a public API (Open-Meteo) for multiple cities, structures it into a clean combined dataset, and handles failures gracefully.

## What It Does

- Fetches real-time weather forecasts for multiple cities via the Open-Meteo API
- Handles failed requests gracefully — a single city's failure doesn't crash the whole collection process; it's simply skipped with a clear message
- Combines multi-city forecast data into a single structured DataFrame
- Calculates summary statistics: average max temperature per city, total precipitation per city
- Saves the final dataset to a CSV file for further use

## Example Output

===Summary===
city
ISB 29.77
RWP 31.09
SM 26.04
Name: temp_max, dtype: float64

Total precipitation by city:
RWP

## How to Run

```bash
pip install pandas requests jupyter
jupyter notebook api-data-collector.ipynb
```

Then run all cells from top to bottom. This creates `data/weather_report.csv` in the project folder.

## Skills Practiced

- Making HTTP requests with proper error handling (`timeout`, `raise_for_status`, `try/except`)
- Gracefully handling failed API calls without crashing the whole pipeline
- Structuring nested JSON responses into clean DataFrames
- Combining multiple data sources with `pd.concat()`
- File/folder automation (organizing output into a dedicated folder)

## Possible Improvements

- Accept a list of cities as a configurable input rather than hardcoded coordinates
- Add retry logic (e.g., attempt a failed request a few times before giving up)
- Schedule this to run automatically on a daily basis to build a historical weather dataset over time