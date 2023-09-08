# Ex02-Outlier
# AIM:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them
# PROCEDURE:
## STEP 1:
Read the given Data.

## STEP 2:
Get the information about the data.

## STEP 3:
Detect the Outliers using IQR method and Z score.

## STEP 4:
Remove the outliers:

## STEP 5:
Plot the datas using box plot.
# PROGRAM & OUTPUT :

### CODE DEVELOPED BY : SRINIDHI SENTHIL 
### REGISTER NUMBER : 212222230148
```
import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/588ee479-de6f-4cca-8bcd-16c54acd5f73)

```
df.describe()
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/d7f5739a-be37-4396-9a3a-576c16800a2a)
```
df.info()
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/6c378338-1da3-4972-81df-34bd5a64693d)
```
df.shape
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/64c8b489-6446-4007-90b0-e44b7023a812)
```
import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/97300c27-9395-4e56-962c-506cc813d31b)
```
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)]
print(newdata)
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/16ecc785-3039-4257-b54e-281b313c8e8f)
```
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/4d6f9f84-f7c5-464e-8f5e-5cbac5d08505)
```
newdata.shape
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/4aaacf89-c47a-449e-932b-7e9485265955)
```
sns.boxplot(x="price_per_sqft",data=newdata)
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/f1ab9ea0-e66a-435b-9367-6ff858cc727b)

```
from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/a33f3485-9e19-4b4c-bc44-87157ba7419f)

```
outlier2=df[(z_score>=3)]
print(outlier2)
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/6b5e377b-93bf-43bf-bcc8-0126a371b88d)

```
newdata2.shape
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/1d9a82aa-6f2d-47e9-91d7-749518913410)
```
sns.boxplot(x="price_per_sqft",data=newdata2)
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/095ba705-3fd8-4964-ad28-b51623e61df3)

```
import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/f3fbd7eb-5278-4f43-bfc5-a4385007f7f6)

```
dataset.describe()
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/1074ed60-0476-4913-8601-9297063ee353)

```
dataset.info()
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/b76cbbf8-8025-4cef-8522-26a6800a156e)

```
import seaborn as sns
sns.boxplot(x='height',data=dataset)
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/c43ee612-d5f6-4e7c-ae1e-7107892d95ae)

```
Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/623a0a6a-6abb-4833-a872-a7c98d04e59e)
```
sns.boxplot(x='height',data=newdata_height)
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/89a8edbf-2434-4c53-a67b-338c4b32db6c)
```
Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/dcd91f6d-c053-4133-9f62-dd31680117f9)
```
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/cce80cc3-0317-4a09-9226-31d4ad21516b)
```
sns.boxplot(x='weight',data=newdata_weight)
```
![image](https://github.com/SRINIDHISENTHILNATHAN/ODD2023---Datascience---Ex-02/assets/121373170/dbc41d80-9e66-4833-8982-0065a77381ca)
