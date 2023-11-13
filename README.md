# Ex-09-Data-Visualization-

## AIM
To Perform Data Visualization on a complex dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.

# CODE
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from google.colab import files
uploaded = files.upload()
df = pd.read_csv("tips.csv")
df
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-09/assets/119477782/2d8e04e1-225a-435d-b530-28a48099bd22)
```
df.isnull().sum()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-09/assets/119477782/5e7bd25e-d4f9-43b1-bb33-04b4dac1a019)
## FINDING OUTLIERS
```
plt.figure(figsize=(5,5))
plt.title("Data with outliers")
df.boxplot()
plt.show()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-09/assets/119477782/f21521ca-e0a6-4912-9c56-ec66f1bef9e8)
## REMOVING OUTLIERS
```
plt.figure(figsize=(8,8))
cols = ['size','tip','total_bill']
Q1 = df[cols].quantile(0.25)
Q3 = df[cols].quantile(0.75)
IQR = Q3 - Q1
df = df[~((df[cols] < (Q1 - 1.5 * IQR)) |(df[cols] > (Q3 + 1.5 * IQR))).any(axis=1)]
plt.title("Dataset after removing outliers")
df.boxplot()
plt.show()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-09/assets/119477782/add2c950-d832-4d1e-a7f5-d12169a5fa6d)
## 1.Which day of the week has the highest total bill amount?
```
sns.barplot(x="day", y="total_bill", data=df)
plt.title("Total Bill Amount by Day of Week")
plt.show()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-09/assets/119477782/0301825d-acb6-459a-8b04-40ffe167a0ed)
## 2.What is the average tip amount given by smokers and non-smokers?
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-09/assets/119477782/790a8a73-43c2-4c0b-b2d3-f57fee0a40e7)
## 3.How does the tip percentage vary based on the size of the dining party?
```
df["tip_pct"] = df["tip"] / df["total_bill"]
sns.scatterplot(x="size", y="tip_pct", data=df)
plt.title("Tip Percentage by Dining Party Size")
plt.show()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-09/assets/119477782/0a83c194-9cd2-4292-8105-a642020ce8e0)
## 4.Which gender tends to leave higher tips?
```
sns.boxplot(x="sex", y="tip", data=df)
plt.title("Tip Amount by Gender")
plt.show()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-09/assets/119477782/454824da-b15e-44c4-b9f0-14264c1321be)
## 5.Is there any relationship between the total bill amount and the day of the week?
```
sns.scatterplot(x="day", y="total_bill", data=df)
plt.title("Total Bill Amount by Day of Week")
plt.show()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-09/assets/119477782/77def542-e6c5-4479-82c9-2022bce79703)
## 6.How does the distribution of total bill amounts vary across different time periods (lunch vs. dinner)?
```
sns.histplot(data=df, x="total_bill", hue="time", element="step", stat="density")
plt.title("Distribution of Total Bill Amounts by Time of Day")
plt.show()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-09/assets/119477782/572fd097-d8fa-4fb3-8514-356fac39e0dd)
## 7.Which dining party size group tends to have the highest average total bill amount?
```
sns.barplot(x="size", y="total_bill", data=df)
plt.title("Average Total Bill Amount by Dining Party Size")
plt.show()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-09/assets/119477782/acc41125-5708-4a32-9531-35abb748a810)
## 8.What is the distribution of tip amounts for each day of the week?
```
sns.boxplot(x="day", y="tip", data=df)
plt.title("Tip Amount by Day of Week")
plt.show()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-09/assets/119477782/c9037f69-2199-45b1-92c5-b73a1ed28ebe)
## 9.How does the tip amount vary based on the type of service (lunch vs. dinner)?
```
sns.violinplot(x="time", y="tip", data=df)
plt.title("Tip Amount by Time of Day")
plt.show()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-09/assets/119477782/73d069fc-2d7f-4153-b798-39809482f25c)
## 10.Is there any correlation between the total bill amount and the tip amount?
```
sns.scatterplot(x="total_bill", y="tip", data=df)
plt.title("Correlation between Tip Amount and Total Bill Amount")
plt.show()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-09/assets/119477782/aa11253d-727c-4712-9456-fd3ef1ed1081)

# RESULT:
Thus, Data Visualization is performed on the given dataset and save the data to a file.
