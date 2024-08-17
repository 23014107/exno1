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
#                         Data cleaning
```
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
  ![image](https://github.com/user-attachments/assets/12b0134a-9092-4528-92df-d9461930b388)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/1fb7dc29-d237-48b2-8107-b2cdb5de4716)
```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/59b8f11e-fde1-49a4-b333-c6ebb81b9f03)
```
df.dropna()
```
![image](https://github.com/user-attachments/assets/c603479e-131e-4934-aa18-0c853551d5ae)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/aba7001b-b340-4c1f-a381-8cf11cb80074)
```
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/50e93532-e5a0-4fdb-b480-895df7319cc7)
```
df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/505b6526-6a3c-4387-8032-e2ce6774b4f3)
```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/39419599-f04f-423f-9b9f-4646f8c32453)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/d8a5de9a-e048-4a80-b10d-6462c8ec9779)

##                                       IQR(Inter Quartile Range)
```
import pandas as pd
ir=pd.read_csv('iris.csv')
ir
```
![image](https://github.com/user-attachments/assets/2e186778-f888-4447-a382-1f5de58364f7)
```
ir.describe()
```
![image](https://github.com/user-attachments/assets/a7995a32-5477-4b55-9a5f-6f1a0ef4744f)
```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/a8a6c224-33f5-4dd7-ad99-aa9057a17726)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/159df35a-3a18-440f-8169-94dc5aa36de2)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/c3b36af2-beca-446d-9d37-b906b587d81c)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/8033d6ff-b4e1-4b09-942c-1fe1628ddaa9)
##                          Z-Score
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```
![image](https://github.com/user-attachments/assets/967782f2-4356-4a6e-8705-df38a57da745)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```
```
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/e46cda83-6bb4-44a2-b283-d9482dab6b71)
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/1a985c7f-3b1d-4e54-aee8-3032c4356e70)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/de8dd960-9ed7-4474-8375-cb08286e2d2e)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/32cb7a0e-abff-4954-9722-6b6699767c3c)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/9746cd59-5602-4905-a96c-009b34d7b714)
```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/c9ef334e-7a30-45a0-970f-343b7fbe09c1)

# Result
         Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
