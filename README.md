# Ex-01_DS_Data_Cleansing


## AIM
To read the given data and perform data cleaning and save the cleaned data to a file. 

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. 
Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information. 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Get the information about the data
### STEP 3
Remove the null values from the data
### STEP 4
Save the Clean data to the file

# CODE and OUTPUT
## Data Cleaning
```py
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
![680e168d-52d3-44fb-b6b5-3f76a974dae3](https://github.com/user-attachments/assets/8adc30dc-e6fa-4ce7-923b-899cdd2beab1)

```py
df.isnull().sum()
```
![72c75082-eb80-4b85-9277-52ee93191ad1](https://github.com/user-attachments/assets/13144857-3459-4933-96d3-07cd6fa8447f)

```py
df.isnull().any()
```
![f14b7806-b025-481e-9378-e320c5f9eb94](https://github.com/user-attachments/assets/d4d731aa-d185-4f8d-84b2-1ff0c54e716c)

```py
df.dropna()
```
![0e44241b-ffff-497d-a9ad-46a18f79ad61](https://github.com/user-attachments/assets/b31c1c7a-d5c5-4b5e-a152-e7bcaa6d8fa0)

```py
f.fillna(0)
```
![85224adf-0d65-41d6-9e4f-fe949fc6aee5](https://github.com/user-attachments/assets/56a32cbf-d6aa-4713-9484-452a985c3e48)

```py
df.fillna(method = 'ffill')
```

![ece8088b-dba9-4403-878a-a38afb5ba394](https://github.com/user-attachments/assets/089ea242-272f-4db3-88c1-3b53e6c18a3c)

```py
df.fillna(method = 'bfill')
```
![adbd632f-5942-4060-8d3d-f973f5b471a9](https://github.com/user-attachments/assets/f9d31d4c-5e67-4006-b883-b5281bb06b10)

```py
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/9a88b1a8-967f-4d68-9c77-894d7d56a784)
## IQR(Inter Quartile Range)
```py
import pandas as pd
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/c65cec8b-a7ba-453d-8043-11f54b91d134)

```py
ir.describe()
```
![image](https://github.com/user-attachments/assets/18034d3a-7649-48bf-81a2-69ba90a69434)

```py
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![adbd632f-5942-4060-8d3d-f973f5b471a9](https://github.com/user-attachments/assets/96f053eb-fbef-4ac3-b1a5-62c09bd42b35)
```py
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/f45130a9-d76e-4bf1-af6d-3bd3552a6cdd)

```py
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/c8963449-c62d-4b40-bbef-94c0a7488dd9)

```py
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/b732cdc5-e35f-4823-b324-cd2072777879)

```py
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/81b792c4-cd80-4032-9c05-22457713dfd0)

## Z-Score

```py
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/c93bec2d-309a-45e4-9a6d-75f39f58ac5c)

```py
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/03c2cfd9-c5cd-4cfc-a359-5d7f02a1ec3e)

```py
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/aaca6523-248b-4508-b13c-fcd82d1fa7eb)

```py
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/f962ad79-8194-4807-9e6f-d17f8af04474)

```py
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/0f6402ad-42e5-44db-9d30-062ce99ea2d8)

```py
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/06ddc9cb-0f93-4790-a2c3-4969e030e7e1)

```py
df1 = df[z<3]
df1
```

![image](https://github.com/user-attachments/assets/da00179b-e8aa-4af7-9bc1-0d4086d550a0)
# RESULT
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
