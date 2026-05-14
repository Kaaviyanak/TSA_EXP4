# Ex.No:04   FIT ARMA MODEL FOR TIME SERIES
# Date: 11.05.2026
### AIM:
To implement ARMA model in python.
### ALGORITHM:
1. Import necessary libraries.
2. Set up matplotlib settings for figure size.
3. Define an ARMA(1,1) process with coefficients ar1 and ma1, and generate a sample of 1000

data points using the ArmaProcess class. Plot the generated time series and set the title and x-
axis limits.

4. Display the autocorrelation and partial autocorrelation plots for the ARMA(1,1) process using
plot_acf and plot_pacf.
5. Define an ARMA(2,2) process with coefficients ar2 and ma2, and generate a sample of 10000

data points using the ArmaProcess class. Plot the generated time series and set the title and x-
axis limits.

6. Display the autocorrelation and partial autocorrelation plots for the ARMA(2,2) process using
plot_acf and plot_pacf.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.graphics.tsaplots import plot_acf, plot_pacf
import warnings
warnings.filterwarnings('ignore')

# Load dataset
df = pd.read_csv('user_behavior_timeseries.csv')

# Prepare time series
df['Date'] = pd.to_datetime(df['Date'], errors='coerce')
df = df.dropna(subset=['Date', 'App Usage Time'])
df = df.sort_values('Date')

time_series = df.groupby('Date')['App Usage Time'].sum()
data = time_series.values

# Automatically safe lag value
safe_lags = (len(data) // 2) - 1
print("Using lags =", safe_lags)

# Plot ACF
plt.figure(figsize=(10,6))
plot_acf(data, lags=safe_lags)
plt.title('ACF - App Usage Time')
plt.show()

# Plot PACF
plt.figure(figsize=(10,6))
plot_pacf(data, lags=safe_lags)
plt.title('PACF - App Usage Time')
plt.show()
```
## OUTPUT:

<img width="733" height="587" alt="image" src="https://github.com/user-attachments/assets/25a17e51-c249-4bfb-b79f-74343dd0294d" />
<img width="715" height="560" alt="image" src="https://github.com/user-attachments/assets/22921f6a-0455-4bfa-ac46-512c58346a58" />


## RESULT:
Thus, a python program is created to fir ARMA Model successfully.
