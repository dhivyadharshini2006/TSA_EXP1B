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
data.plot(kind='line')

```

### OUTPUT:
ORGINAL DATA:
<img width="910" height="171" alt="image" src="https://github.com/user-attachments/assets/f77922a8-0fd2-45ab-bd46-f962522640a4" />


REGULAR DIFFERENCING:
<img width="917" height="151" alt="image" src="https://github.com/user-attachments/assets/21dc3ebb-099f-4303-b538-74a4f74b33fd" />



SEASONAL ADJUSTMENT:
<img width="913" height="158" alt="image" src="https://github.com/user-attachments/assets/2f60b0bc-c141-4991-a49a-701f54c17110" />



LOG TRANSFORMATION:


<img width="920" height="150" alt="image" src="https://github.com/user-attachments/assets/cbb88668-361a-4eed-8631-ffac4712d6d5" />

LOG TRANSFORMATION AND REGULAR DIFFERENCING:




<img width="913" height="149" alt="image" src="https://github.com/user-attachments/assets/62439c85-6340-497a-88fd-cb7c51c02d90" />


LOG TRANSFORMATION AND REGULAR AND SESONAL DIFFERENCING:



<img width="939" height="160" alt="image" src="https://github.com/user-attachments/assets/9db08570-8871-485f-8647-f664f51f4709" />

### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
