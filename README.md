
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION

### AIM:
To Illustrates how to perform time series analysis and decomposition on the goodreadsbooks dataset
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
### Developed by: R Guruprasad
### Register no:212222240033
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

data = pd.read_csv('goodreads_books.csv', nrows=50)

data['publication_date'] = pd.to_datetime(data['publication_date']) 

monthly_data = data.resample('M', on='publication_date')['ratings_count'].sum().reset_index()

monthly_data.set_index('publication_date', inplace=True)

decomposition = seasonal_decompose(monthly_data, model='additive')

# Step 5: Plot the data
plt.figure(figsize=(10, 30))  # Change this to a square shape

# Original Data
plt.subplot(411)
plt.plot(monthly_data, label='Monthly Ratings Count')
plt.legend(loc='upper left')
plt.title('Monthly Ratings Count')

# Trend Plot
plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Trend Plot')

# Seasonal Plot
plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonal Plot')

# Residual Plot
plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual Plot')

plt.tight_layout()
plt.show()

```

### OUTPUT:

FIRST FIVE ROWS:

![{FCADBF60-E218-4149-A32F-5B5C5B9BF498}](https://github.com/user-attachments/assets/402a1487-8cab-4dc2-b026-d7c55a4f22fd)


PLOTTING THE DATA:

![{76B5D7CA-015E-4613-BE06-89F31DDFFC77}](https://github.com/user-attachments/assets/c10ecbe7-95ec-4fb4-b7d1-8ea6f8a6de70)


SEASONAL PLOT REPRESENTATION :

![{A3F0FBD4-F8D8-4EA9-8860-945AA7272840}](https://github.com/user-attachments/assets/bfed3db5-bd30-4ad8-970a-d9928282150d)


TREND PLOT REPRESENTATION :

![{19693FB6-28F2-473D-B106-801B98640574}](https://github.com/user-attachments/assets/199b43a0-b38f-4077-a7b9-1280b66b91a2)


OVERAL REPRESENTATION:

![{00D6F852-0B44-4D0B-A521-16CDB2488007}](https://github.com/user-attachments/assets/93b373da-a3b1-4505-8e42-95d03f446cff)



### RESULT:
Thus, the python code for the time series analysis and decomposition is successfully implemented.
