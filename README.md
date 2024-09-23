# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average .

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
Developed by : YOHESH KUMAR R.M
Reg. No      : 212222240118 
```
``` python
# Import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load the dataset
data = pd.read_csv('Microsoft_Stock.csv')

# Convert 'Date' column to datetime format and set it as index
data['Date'] = pd.to_datetime(data['Date'])
data.set_index('Date', inplace=True)

# Display the first five rows of the dataset
print("FIRST FIVE ROWS:")
print(data.head())

# Resample the data to get monthly average of the 'Close' price
monthly_avg = data['Close'].resample('M').mean()

# Plot the original monthly average closing price
plt.figure(figsize=(10, 6))
plt.plot(monthly_avg, label='Monthly Average Closing Price')
plt.title('PLOTTING THE DATA: Monthly Average Closing Price')
plt.xlabel('Date')
plt.ylabel('Price')
plt.legend()
plt.grid(True)
plt.show()

# Specify the period for decomposition (12 months for yearly seasonality)
period = 12

# Perform time series decomposition using a multiplicative model
result = seasonal_decompose(monthly_avg, model='multiplicative', period=period)

# Plot the seasonal component
plt.figure(figsize=(10, 6))
plt.plot(result.seasonal, label='Seasonal Component', color='green')
plt.title('SEASONAL PLOT REPRESENTATION')
plt.xlabel('Date')
plt.ylabel('Seasonality')
plt.legend()
plt.grid(True)
plt.show()

# Plot the trend component
plt.figure(figsize=(10, 6))
plt.plot(result.trend, label='Trend Component', color='orange')
plt.title('TREND PLOT REPRESENTATION')
plt.xlabel('Date')
plt.ylabel('Trend')
plt.legend()
plt.grid(True)
plt.show()

# Overall decomposition plot (trend, seasonal, residual)
plt.figure(figsize=(10, 8))
result.plot()
plt.suptitle('OVERALL REPRESENTATION: Decomposition of Time Series', y=1.02)
plt.tight_layout()
plt.show()

```
### OUTPUT:

#### FIRST FIVE ROWS:
![image](https://github.com/user-attachments/assets/a4f008fc-2e97-48f1-a412-93f513012d82)

#### PLOTTING THE DATA:
![image](https://github.com/user-attachments/assets/4a94d994-c9bd-452c-9ef1-34bf8efab557)

#### SEASONAL PLOT REPRESENTATION :
![image](https://github.com/user-attachments/assets/ac4230f9-ffa7-4dda-a6f7-e6e352d0af5d)

#### TREND PLOT REPRESENTATION :
![image](https://github.com/user-attachments/assets/536afa30-f7c5-43d8-99b8-bf64637e5687)

#### OVERAL REPRESENTATION:
![image](https://github.com/user-attachments/assets/2a456b7a-efac-4df2-bfe6-a14792497bfd)

### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
