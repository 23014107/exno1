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
```
import pandas as pd
df=pd.read_csv('Loan_data.csv')
df
```
## Output
![Screenshot 2025-03-26 155457](https://github.com/user-attachments/assets/90c11d57-7339-4fcd-9754-44ee9b943ae0)

```
df.head(5)
```
#  Output
![Screenshot 2025-03-26 155548](https://github.com/user-attachments/assets/7b49eb84-9a7b-4c0b-9845-de1465d5a9bf)
```
df.tail(5)
```
# Output
![Screenshot 2025-03-26 155633](https://github.com/user-attachments/assets/71847378-8865-4526-8523-6eed321e2449)


```
df.info()
```
# Output
![Screenshot 2025-03-26 155722](https://github.com/user-attachments/assets/1542f428-1a89-4514-9aea-41fdbd388046)

```
df.describe()
```
# Output
![Screenshot 2025-03-26 155758](https://github.com/user-attachments/assets/0ed28fa6-a673-4650-a37a-296b4c02ba86)

```
df.shape
```
# Output
![Screenshot 2025-03-26 155843](https://github.com/user-attachments/assets/49c67663-4402-4f48-b9fa-7fd0c9cc9111)

```
df.isnull().sum()
```
# Output
![Screenshot 2025-03-26 155918](https://github.com/user-attachments/assets/5bb651cb-d636-42e0-8f12-b5301dd91895)

```
df.nunique()
```
# Output
![Screenshot 2025-03-26 155950](https://github.com/user-attachments/assets/ec975099-2b41-49ca-9b19-deec701539e0)

```
mn=df.Credit_History.mean()
mn
```
# Output
![Screenshot 2025-03-26 160041](https://github.com/user-attachments/assets/4b215d46-9d0b-474f-9c07-3187e7d25ec6)

```
df['Gender'].value_counts()
```
# Output
![image](https://github.com/user-attachments/assets/d0824702-86dd-44c2-af08-e9f5a5b7f7b2)

```
df.Credit_History.fillna(mn,inplace=True)
df.LoanAmount.fillna(0)
```
# Output
![Screenshot 2025-03-26 160146](https://github.com/user-attachments/assets/82d8ebff-ecfd-4900-8258-2cdefe12e51d)

```
min=df.LoanAmount.min()
min
```
# Output
![Screenshot 2025-03-26 160227](https://github.com/user-attachments/assets/5b4621ee-0f4d-403c-9c3a-4bebe8d551b6)
```
df.LoanAmount.fillna(min,inplace=True)
df
```
# Output
![Screenshot 2025-03-26 160637](https://github.com/user-attachments/assets/324c9561-a7e2-4aeb-8672-520c05a0ab96)


```
df.isnull()
```
# Output
![Screenshot 2025-03-26 160709](https://github.com/user-attachments/assets/1a371866-fc43-41bc-9b24-cde74902501a)

```
import pandas as pd
import seaborn as sns
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
```
# Output
![Screenshot 2025-03-26 160750](https://github.com/user-attachments/assets/b4e69f37-0a00-4b0c-b518-301d676122e6)

```
sns.boxplot(data=af)
```
# Output
![Screenshot 2025-03-26 160832](https://github.com/user-attachments/assets/b7f3b1ef-237a-4994-b89c-b3a6649d6ff0)

```
sns.scatterplot(data=af)
```
# Output
![Screenshot 2025-03-26 160915](https://github.com/user-attachments/assets/e47779a0-c1e5-4ffc-a4b4-53e0ba34d042)

```
q1=af.quantile(0.25)
q2=af.quantile(0.5)
q3=af.quantile(0.75)
iqr=q3-q1
iqr
```
# Output
![Screenshot 2025-03-26 160958](https://github.com/user-attachments/assets/133441e4-4d34-4c8d-89a3-84a33375f658)

```
low=q1-1.5*iqr
low
```
# Output
![Screenshot 2025-03-26 161029](https://github.com/user-attachments/assets/fdf18952-304e-4819-9b1e-ff8a92183fb9)

```
high=q3+1.5*iqr
high
```
# Output
![Screenshot 2025-03-26 161103](https://github.com/user-attachments/assets/ffd65f5a-c675-47a5-ae3e-a7e8635df9ad)

```
af=af[((af>=low)&(af<=high))]
af
```
# Output
![Screenshot 2025-03-26 161139](https://github.com/user-attachments/assets/f88346cc-3307-44a9-8adc-ffeeacd09d9f)

```
af.dropna()
```
# Output
![Screenshot 2025-03-26 161215](https://github.com/user-attachments/assets/080facec-3f79-4d87-9ed7-13dafbae70de)

```
sns.boxplot(data=af)
```
# Output
![Screenshot 2025-03-26 161245](https://github.com/user-attachments/assets/a887bd83-2317-41b5-8226-58b83beac773)

```
data=[1,12,15,18,21,24,27,20,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81,84,87,90,93,96,99,158]
df=pd.DataFrame(data)
df
```
# Output
![Screenshot 2025-03-26 161339](https://github.com/user-attachments/assets/c99755ac-6214-4d93-94d0-aa91d26fe9d8)

```
import numpy as np
from scipy import stats
z=np.abs(stats.zscore(df))
z
```
# Output
![Screenshot 2025-03-26 161430](https://github.com/user-attachments/assets/f2c1d160-bd97-467f-92a3-d41c612253e3)



# Result
Thus, we have read the given data and performed data cleaning and saved the cleaned data to a file successfully.
