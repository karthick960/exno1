# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```python
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![image](https://github.com/user-attachments/assets/d9eab364-a23b-4668-bbe9-31792f9db375)

```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/b3470059-769f-4d8a-a641-198078cccc9f)
```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/492898a4-f5b2-43c7-930e-6a810f9f741d)
```
df.dropna()
```
![image](https://github.com/user-attachments/assets/5d18ca18-9fb3-44f3-9923-e80e0a7bbdb0)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/d2c41641-b4e8-4d90-b439-1a3cdc1f406c)
```
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/b4bb32b7-1c8d-42ff-a0fc-f3d52a709cad)
```
df.fillna(method='bfill')
```
![image](https://github.com/user-attachments/assets/9608e086-9f8b-4a9c-a59c-b2e572a7607f)
```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/1d1605f7-874d-494e-b615-2300ec04faad)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/29107ff3-3ff8-46ac-a784-2184fe59bae0)


# IOR(inter Quartile range)


```
import pandas as pd
ir=pd.read_csv('/content/iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/a6e43f3a-34b4-4af8-9826-da36756c4cd2)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/55b5a606-1f92-4f52-8967-f575558843f1)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/64a8726a-ae9d-4452-8ad9-96fdd655b994)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/76d1c706-f835-4fe5-a39d-d8efadf4e544)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/b7960b1f-d3ea-4d2d-bc64-b8e567c560ba)

# Z-Score

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/c8336556-1c7b-4021-8179-9abaedcd97b2)
```
df=pd.read_csv("heights.csv")
q1=df['height'].quantile(0.25)
q2=df['height'].quantile(0.5)
q3=df['height'].quantile(0.75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/afc3a5d4-4f0e-420c-9e9d-3e03638cbc69)
```
low=q1=1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/e578622b-8daa-4e16-9770-01ac01dde1fa)
```
high=q3+1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/cf3695ba-d49a-4f57-ad2b-b7ca3cc8a034)

```
df1=df[((df['height']>=low)&(df['height']<=high))]
df1
```
![image](https://github.com/user-attachments/assets/89ed60c9-75fd-4c12-8c63-c5de38a7f608)
```
z=np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/322f4cb3-3e55-4fad-b6ef-51932fd43f7a)
```
df1=df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/6cf8475b-349b-4f1d-81c7-647a2504d389)

# Result
Thus we have cleaned the data and remove the outliers by detection using IQR and Z-score method.
