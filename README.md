# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date:18/08/2025 

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data=pd.read_csv('gold_price_data.csv')
data.head()
data['Date']=pd.to_datetime(data['Date']) 
data.set_index('Date', inplace=True)
```
```
data['Value_diff'] = data['Value'] - data['Value'].shift(1)
result = seasonal_decompose(data['Value'], model='additive', period=12)
data['Value_sea_diff'] = result.resid
data['Value_log'] = np.log(data['Value'])
data['Value_log_diff'] = data['Value_log'] - data['Value_log'].shift(1)
result_log_diff = seasonal_decompose(data['Value_log_diff'].dropna(), model='additive', period=12)
data['Value_log_seasonal_diff'] = result_log_diff.resid
plt.figure(figsize=(16, 16))
plt.subplot(6, 1, 1)
plt.plot(data['Value'], label='Original')
plt.legend(loc='best')
plt.title('Original Gold Price Data')
plt.xlabel('Date')
plt.ylabel('Value')
```
```
plt.subplot(6, 1, 2)
plt.plot(data['Value_diff'], label='Regular Difference')
plt.legend(loc='best')
plt.title('Regular Differencing')
plt.xlabel('Date')
plt.ylabel('Value')

```
```
plt.subplot(6, 1, 3)
plt.plot(data['Value_sea_diff'], label='Seasonal Adjustment')
plt.legend(loc='best')
plt.title('Seasonal Adjustment')
plt.xlabel('Date')
plt.ylabel('Value')
```
```
plt.subplot(6, 1, 4)
plt.plot(data['Value_log'], label='Log Transformation')
plt.legend(loc='best')
plt.title('Log Transformation')
plt.xlabel('Date')
plt.ylabel('Value')
```
```
plt.subplot(6, 1, 5)
plt.plot(data['Value_log_diff'], label='Log Transformation and Regular Differencing')
plt.legend(loc='best')
plt.title('Log Transformation + Regular Differencing')
plt.xlabel('Date')
plt.ylabel('Value')

```
```
plt.subplot(6, 1, 6)
plt.plot(data['Value_log_seasonal_diff'], label='Log + Regular + Seasonal Differencing')
plt.legend(loc='best')
plt.title('Log Transformation + Regular + Seasonal Differencing')
plt.xlabel('Date')
plt.ylabel('Value')
plt.tight_layout()
plt.show()

```
```
data['Value'].plot(kind='line', title='Gold Price Over Time', figsize=(12,6))
plt.xlabel('Date')
plt.ylabel('Value')
plt.show()

```

### OUTPUT:


REGULAR DIFFERENCING:
<img width="729" height="182" alt="image" src="https://github.com/user-attachments/assets/daa3ac07-2225-4459-9fcb-5dccde1bdc76" />



SEASONAL ADJUSTMENT:
<img width="748" height="175" alt="image" src="https://github.com/user-attachments/assets/d4bc117a-7301-4a25-b2a7-805f01d27aa1" />


LOG TRANSFORMATION:
<img width="731" height="186" alt="image" src="https://github.com/user-attachments/assets/3c0c68bc-ad98-423f-b3f6-fb265a4f2c48" />



### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
