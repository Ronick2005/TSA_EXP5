# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on the daily website visitors dataset.

### ALGORITHM:
1. Import the required packages like pandas, matplotlib, and statsmodels.
2. Read the data using pandas from the provided website visitors dataset.
3. Convert the 'Date' column to a datetime object and set it as the index.
4. Perform seasonal decomposition using the seasonal_decompose function on the Page.Loads column with a weekly periodicity (7 periods for daily data).
5. Plot the data components: observed, trend, seasonal, and residual plots.
6. Display the overall results through graphical representations.

### PROGRAM:
```py
import pandas as pd

file_path = '/content/daily_website_visitors.csv'
df = pd.read_csv(file_path)

df.head()

df['Page.Loads'] = df['Page.Loads'].str.replace(',', '').astype(int)
df['Unique.Visits'] = df['Unique.Visits'].str.replace(',', '').astype(int)
df['First.Time.Visits'] = df['First.Time.Visits'].str.replace(',', '').astype(int)
df['Returning.Visits'] = df['Returning.Visits'].str.replace(',', '').astype(int)

df['Date'] = pd.to_datetime(df['Date'], format='%m/%d/%Y')
df.set_index('Date', inplace=True)

from statsmodels.tsa.seasonal import seasonal_decompose
import matplotlib.pyplot as plt

decomposition = seasonal_decompose(df['Page.Loads'], model='additive', period=7)

plt.figure(figsize=(10, 4))
decomposition.observed.plot(color='blue')
plt.title('Observed')
plt.ylabel('Page Loads (Observed)')
plt.show()

plt.figure(figsize=(10, 4))
decomposition.trend.plot(color='green')
plt.title('Trend')
plt.ylabel('Page Loads (Trend)')
plt.show()

plt.figure(figsize=(10, 4))
decomposition.seasonal.plot(color='red')
plt.title('Seasonal')
plt.ylabel('Page Loads (Seasonal)')
plt.show()

plt.figure(figsize=(10, 4))
decomposition.resid.plot(color='purple')
plt.title('Residual')
plt.ylabel('Page Loads (Residual)')
plt.show()

```
### OUTPUT:
#### FIRST FIVE ROWS:
![image](https://github.com/user-attachments/assets/82ac3452-f2a0-49ef-93be-3cf0853c8972)

#### PLOTTING THE DATA:
![image](https://github.com/user-attachments/assets/f783b2e5-2a48-4f6d-a899-7c8a6bdca15b)

#### SEASONAL PLOT REPRESENTATION :
![image](https://github.com/user-attachments/assets/3f2bed28-6c3c-45df-8565-e9c454431992)

#### TREND PLOT REPRESENTATION :
![image](https://github.com/user-attachments/assets/c09a40f1-1ef1-4e39-b92d-3b6f73b37f37)

#### RESIDUAL PLOT REPRESENTATION:
![image](https://github.com/user-attachments/assets/4c772203-1644-4cdb-a618-e086aba1d4b7)

### RESULT:
Thus we have created the python code for the time series analysis and decomposition on the daily website visitors dataset.
