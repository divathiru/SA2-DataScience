# SA2-Data-Science

## AIM:

To perform data preprocessing, detect and remove outliers using Boxplot and IQR methods, and carry out univariate and multivariate analysis using Count Plot and Distribution Plot on the Toyota car dataset.
```
Program Developed by : K.Thirumurugan
Register Number : 212224110057
```
## EQUIPMENTS REQUIRED:

1.Hardware – PCs

2.Software – Anaconda (Python 3.7) / Jupyter Notebook

## ALGORITHM:

1.Import necessary libraries – pandas, matplotlib, seaborn, numpy.

2.Load the dataset (Toyota.csv) and preview the data.

3.Perform data cleaning –

  -Drop null values if any.

  -Remove duplicates if present.

  -Check for inconsistencies or irrelevant columns.

4.Detect Outliers using Boxplot Method –

  -Plot boxplots for numerical columns like Price, Age, KM, etc.

  -Visually inspect and identify outliers.

5.Remove Outliers using IQR Method –

  -Calculate Q1, Q3, and IQR for each numeric feature.

  -Remove rows where values fall below (Q1 - 1.5 * IQR) or above (Q3 + 1.5 * IQR).

6.Perform Univariate Analysis using Count Plot –

  -Use seaborn.countplot() for categorical variables like FuelType.

7.Perform Multivariate Analysis using Dist Plot –

  -Use sns.histplot() with hue parameter for comparing numerical features across categories.

## PROGRAM / OUTPUT:

```
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
df=pd.read_csv("Toyota.csv")
df
```
![image](https://github.com/user-attachments/assets/e516315a-dae2-40d1-97d8-25bcdc7ca4a1)

```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/576b3226-8a9a-4b2f-b5cf-254e2967740e)
```
df.drop(columns=["Unnamed: 0"], inplace=True)
df.isna().sum()
```
![image](https://github.com/user-attachments/assets/50518641-e8d6-46f5-9fb1-c7536d1e0821)
```
df.dtypes
```
![image](https://github.com/user-attachments/assets/32975efd-c97e-4e21-9b59-e666c3eb076e)
```
df.columns()
```
![image](https://github.com/user-attachments/assets/c998f32a-79ad-4f9a-85b6-75da799ac694)
```
df = df.dropna()
```
![image](https://github.com/user-attachments/assets/1fc63e6b-58b4-446b-bac1-bf28e21becb6)
```
df = df.drop_duplicates()
```
![image](https://github.com/user-attachments/assets/b5d85b33-55ea-40fd-a84d-cfad887fe8ed)

**BOXPLOT METHOD:**

```
plt.figure(figsize=(15, 5))
sns.boxplot(y=df['Price'], color='cyan')
plt.title("Boxplot - Price")
plt.show()
```
![image](https://github.com/user-attachments/assets/e90736d1-5f9c-46fe-8373-93708af113ae)
```
sns.boxplot(y=df['Age'], color='purple')
plt.title("Boxplot - Age")
plt.show()
```
![image](https://github.com/user-attachments/assets/2ecbf1fc-a251-46c0-9bd1-32a81741035a)
```
sns.boxplot(y=df['KM'], color='yellow')
plt.title("Boxplot - KM")
plt.show()
```
![image](https://github.com/user-attachments/assets/1f10266f-d580-4d83-8cf6-d815d22170cf)

**IQR METHOD:**
```
def remove_outliers_iqr(data, column):
    Q1 = data[column].quantile(0.25)
    Q3 = data[column].quantile(0.75)
    IQR = Q3 - Q1
    lower = Q1 - 1.5 * IQR
    upper = Q3 + 1.5 * IQR
    return data[(data[column] >= lower) & (data[column] <= upper)]

df = remove_outliers_iqr(df, 'Price')
df = remove_outliers_iqr(df, 'Age')
df = remove_outliers_iqr(df, 'KM')
```
![image](https://github.com/user-attachments/assets/3de34be7-be03-4829-82e4-20624984ea56)

**COUNT PLOT:**
```
plt.figure(figsize=(6, 4))
sns.countplot(x='FuelType', data=df, palette='Set2')
plt.title("Count Plot - Fuel Type")
plt.show()
```
![image](https://github.com/user-attachments/assets/1433572c-4e14-471a-8e6c-45bb08506606)

**DISPLOT:**
```
plt.figure(figsize=(10, 6))
sns.histplot(data=df, x='Price', hue='FuelType', kde=True, palette='husl')
plt.title("Distribution Plot of Price by Fuel Type")
plt.show()
```
![image](https://github.com/user-attachments/assets/48ba8cd7-0c64-4152-89db-4c399d1f8e1e)

## RESULT:

The program was successfully executed. Data was cleaned, outliers were detected and removed using boxplot and IQR methods, and both univariate and multivariate analyses were performed using count plot and distplot.
