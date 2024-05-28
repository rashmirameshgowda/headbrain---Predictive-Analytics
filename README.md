#installing dependencies
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
plt.rcParams['figure.figsize'] = (20.0 , 10.0)

#import and explore the dataset
data = pd.read_csv("C:/Users/Rashmi/Downloads/headbrain.csv")
print(data.shape)
data.head()

#Assign values from dataset col to variables
X = data['Head Size(cm^3)']
Y = data['Brain Weight(grams)']

n = len(X)

numer = 0
denom = 0

#m = (Sum(x-x`)(y-y`))/(Sum(x-x`)^2)
for i in range(n):
    numer += (X[i]-mean_x)*(Y[i]-mean_y)
    denom += (X[i]-mean_x)**2
m = numer/denom
c = mean_y - (m*mean_x) ---#y = mx+c
print(m,c) 

#find min and max values to plot graph
max_x = np.max(X) + 100
min_x = np.min(X) - 100

#Return evenly spaced numbers over a specified interval.
#calculating line values x & y
x = np.linspace(min_x, max_x, 1000)
y = m*x + c

#plot and scatter plot, assigning labels and legend
plt.plot(x, y, color = 'b', label = 'Reg line')
plt.scatter(X, Y, color = 'r', label = 'scatter plot')
plt.xlabel('Head Size(cm^3)')
plt.ylabel('Brain Weight(grams)')
plt.legend()
plt.show()
