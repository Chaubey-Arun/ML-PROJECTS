**Imagine you have the following DataFrame**

import pandas as pd

# Example DataFrame
data = {
    'Marketing Spend': [100, 200, 300, 400, 500],
    'Store Traffic': [500, 600, 700, 800, 900],
    'Sales': [150, 200, 250, 300, 350]
}

df = pd.DataFrame(data)
print(df)

**DATA FRAME :**

   Marketing Spend  Store Traffic  Sales
0              100            500    150
1              200            600    200
2              300            700    250
3              400            800    300
4              500            900    350


# Step 1: Identify the target variable (y):
In this case, the target variable is Sales, which is the dependent variable.

# Step 2: Identify the feature variables (X):
The feature variables are Marketing Spend and Store Traffic, which are the independent variables.

# Step 3: Split into X and y:**
# Define the target variable (y)
y = df['Sales']

# Define the feature variables (X)
X = df['Marketing Spend']



# If you change the order of the variables on the left-hand side when unpacking the results from the linregress function,
# it will not assign the values correctly because each value returned by linregress corresponds to a specific statistical result in the original order.

# Let's break it down:

# Original Order of Returned Values from linregress(x, y):
# When you call linregress(x, y), it returns five values in the following specific order:

**slope**
**intercept**
**r_value (correlation coefficient)**
**p_value**
**std_err (standard error of the slope)**
**So, the original assignment is like this:****

mport numpy as np 
import matplotlib.pyplot as plt
from scipy.stats import linregress

x = df['Sales']
y= df['Marketing Spend']

Slope ,intersept,r_value, p_value,std_err = linregress(x,y)

print(Slope,intersept,r_value,p_value,std_err)
**10.376861780533357 262.5910805206704 0.7202281090627562 7.209361483313792e-06 1.8889132296443216**


pridicted_y = Slope * x + intersept
pridicted_y



# 1. Graph Representation of Variance in ( Y )
Consider these five actual data points (●) along the ( Y )-axis:
(SST - Total Variance)¶
 Y-axis ↑
  |
10|       ●   
  |       
  |       ●   
  |       
  |       ●   Mean (Ȳ)  
  |       
  |       ●   
  |       
  |       ●   
  +-------------------> X-axis


# 2. SSR - Variation Explained by the Regression Model
**
 Y-axis ↑
  |
10|       ●  
  |       ◌   (Predicted Ŷ)
  |       
  |       ●   
  |       ◌   
  |       ●   Mean (Ȳ)  
  |       ◌   
  |       ●   
  |       ◌   
  +-------------------> X-axis**

# 3. SSE - Unexplained Error
   Y-axis ↑
  |
10|       ● ← Residual Error (Actual Y - Predicted Ŷ)
  |       ◌  
  |       
  |       ●   
  |       ◌   
  |       ●   Mean (Ȳ)  
  |       ◌   
  |       ●   
  |       ◌   
  +-------------------> X-axis

# 4. Summary: How They Relate
[ SST = SSR + SSE ]**

y_mean=np.mean(y)
sse =np.sum(( y - pridicted_y)*2)
ssr =np.sum(( pridicted_y- y_mean )**2)
sst =np.sum((y-y_mean)**2)

![image (8)](https://github.com/user-attachments/assets/9ac201b3-76c2-40bb-9b31-1c3bcc337f70)
# Plot the data and the regression line
plt.scatter(x, y, label='Original Data')
plt.plot(x, pridicted_y, label='Regression Line', color='red')
plt.xlabel('Bill in $')
plt.ylabel('Tip Amount in $')
plt.title('Linear Regression')
plt.legend()

# Annotate the regression equation on the chart
equation = f'y = {Slope:.4f}x + {intersept:.4f}'
plt.annotate(equation, xy=(0.1, 0.7), xycoords='axes fraction', fontsize=12)

plt.show()

# Display regression results
print("Slope:", Slope)
print("Intercept:", intersept)
print("R-squared:", r_value ** 2)
print("P-Value:", p_value)
print("Standard Error:", std_err)
print("SSR (Sum of Squares Regression):", ssr)
print("SST (Total Sum of Squares):", sst)
print("SSE (Sum of Squares Error):", sse)
