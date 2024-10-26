---
title: "EventAnalysis"
collection: open access
type: "R-based"
permalink: /open access/2024-fall-open access-4
venue: "Event study"
date: 2024-10-19
---

`EventAnalysis` is an R package designed for event study analysis, helping researchers and analysts to assess the impact of events on stock returns, financial indicators, and other metrics. This package is especially useful for financial market research, allowing users to flexibly set event windows and benchmarks.

More information can be found in [here](https://github.com/LINGYUAN1201/EventAnalysis)

## Installation

```R
#Install from GitHub
install.packages("devtools")
devtools::install_github("LINGYUAN1201/EventAnalysis")
```

## Features
The EventAnalysis package offers a range of features to make event studies straightforward and efficient, including:

*   Event Window Setting: Supports customization of the pre- and post-event windows to evaluate event impact flexibly.
*   Return Calculation: Calculates cumulative returns, abnormal returns, and cumulative abnormal returns (CAR).
*   Statistical Testing: Includes built-in statistical tests to assess the significance of event impacts.
*   Industry Comparison: Supports comparative analysis between high- and low-emission industries.

## Quick Start
The following example demonstrates how to conduct a basic event study using the EventAnalysis package:

### Load the Package

```R
library(EventAnalysis)
```

### Data Preparation

Currently this package can run the CAR calculated by the market model and the market adjustment model, so you need to prepare three data files:

*   Event.xlsx: This file mainly contains the date of the Event for each company

*   Firm.xlsx: This file mainly includes the closing prices and earnings of each company over a period of time

*   Market.xlsx: This file mainly contains Market index data

### Load data
```R
data <- load_and_prepare_data("Event.xlsx", "Firm.xlsx", "Market.xlsx")
event_df <- data$event_df
merged_df <- data$merged_df
```
### Compute the CAR of multiple events and generate a CSV file
```R
car_results <- analyze_events(event_df, merged_df, estimation_window = 120, event_window = c(-10, 10))
```
### Calculate the daily AR of the event window
```R
ar_df <- calculate_daily_ar(event_df, merged_df, estimation_window = 120, event_window = c(-10, 10))
```
### Calculate daily average CAR and perform t test
```R
daily_mean_results <- daily_mean_t_test(ar_df, event_window = c(-10, 10))
```

## Others
This R package is based on Python code for the same functionality, designed with the ease of use of R in mind. If you are interested in this content, you can contact me directly.

### Part of code
```python
import pandas as pd
import numpy as np
from statsmodels.regression.linear_model import OLS
from statsmodels.tools import add_constant
from scipy import stats
from scipy.stats import binomtest, wilcoxon, ttest_1samp
from google.colab import files
from openpyxl import load_workbook
from openpyxl.styles import PatternFill

# Step 1: Load and clean the data
def load_and_prepare_data(event_file, firm_file, market_file):
    event_df = pd.read_excel(event_file).rename(columns=str.lower)
    firm_df = pd.read_excel(firm_file).rename(columns=str.lower)
    market_df = pd.read_excel(market_file).rename(columns=str.lower)
    
    for df in [event_df, firm_df, market_df]:
        df.columns = df.columns.str.strip()
    event_df['date'] = pd.to_datetime(event_df['date'])
    firm_df['date'] = pd.to_datetime(firm_df['date'])
    market_df['date'] = pd.to_datetime(market_df['date'])
    
    merged_df = pd.merge(firm_df, market_df, on='date')
    return event_df, merged_df

# Step 2: Define window parameters
ESTIMATION_WINDOW = 120
EVENT_WINDOW = (-10, 10)
WINDOW_LENGTH = EVENT_WINDOW[1] - EVENT_WINDOW[0] + 1

# Step 3: Define the calculation functions for CAR and statistical tests
def calculate_statistics(ar):
    CAR = ar.sum()
    if len(ar) > 1 and ar.std(ddof=1) > 0:
        t_stat = CAR / (ar.std(ddof=1) / np.sqrt(len(ar)))
        p_value = stats.t.sf(np.abs(t_stat), len(ar) - 1) *2 # two-tailed test
    else:
        t_stat, p_value = np.nan, np.nan
    return CAR, t_stat, round(p_value, 5)

...

```

My email: LingYUAN1201@outlook.com
