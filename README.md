# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
#### Name: SHYAM S
#### Register.No: 212223240156

## AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

## ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

## PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

data = pd.read_csv("/content/index_1.csv")

data['datetime'] = pd.to_datetime(data['datetime'])

daily_revenue = data.set_index('datetime').resample('D')['money'].sum()

decomposition = seasonal_decompose(daily_revenue, model='additive', period=7)

plt.figure(figsize=(10, 12))

# Original
plt.subplot(411)
plt.plot(daily_revenue, label='Daily Revenue')
plt.legend(loc='upper left')
plt.title('Daily Coffee Shop Revenue')

# Trend
plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Trend')

# Seasonality
plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonality')

# Residual
plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual')

plt.tight_layout()
plt.show()
```
## OUTPUT:
<img width="990" height="1189" alt="image" src="https://github.com/user-attachments/assets/29068bff-5144-4a21-bc73-4c408c4ea15d" />

## RESULT:
Thus we have created the python code for the time series analysis and decomposition.
