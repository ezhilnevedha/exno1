# Exno:1
Data Cleaning Process
### NAME: EZHIL NEVEDHA K
### REG.NO: 212223230055
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
df=pd.read_csv("Loan_data.csv")
df
```
![image](https://github.com/user-attachments/assets/ccb615f9-870b-4ea5-87bf-fe55059ab3aa)
```
df.isnull()
df.notnull()
df.dropna(axis=1)
df.dropna(axis=0)
```
![image](https://github.com/user-attachments/assets/bca2c12c-661f-4977-9726-40aa0bd7976e)
![image](https://github.com/user-attachments/assets/67275411-029b-4c1c-9380-511759c5cf82)
```
df.fillna(0)
df.fillna(method="ffill")
df.fillna(method="bfill")
```
![image](https://github.com/user-attachments/assets/74806147-5804-4eb7-a04c-ed3d6e301082)
![image](https://github.com/user-attachments/assets/f73bd060-30f1-4b5f-a784-455838aba7ad)
```
df['Credit_History'].fillna(value=df['Credit_History'].mean())
df.dropna()
```
![image](https://github.com/user-attachments/assets/7a3f495e-d51a-4b3a-a669-09c4136c5897)
```
import seaborn as sns
import numpy as np
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
af=pd.DataFrame(age)
af
sns.boxplot(data=af)
sns.scatterplot(data=af)
```
![image](https://github.com/user-attachments/assets/24a7d508-ce23-4c47-865e-6506df96d2b0)
![Screenshot 2025-03-12 224033](https://github.com/user-attachments/assets/16315a2b-ff94-4d5a-aa04-5bb6457c2cad)
```
q1=af.quantile(0.25) 
q2=af.quantile(0.5) 
q3=af.quantile(0.75) 
iqr=q3-q1 
iqr

Q1=np.percentile(af,25)
Q3=np.percentile(af,75)
IQR=Q3-Q1
IQR

lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
lower_bound

lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
lower_bound
upper_bound

outliers=[x for x in age if x<lower_bound or x>upper_bound]
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR;",IQR)
print("Lower bound:",lower_bound)
print("Upper bound:",upper_bound)
print("Outliers:",outliers)
```

![image](https://github.com/user-attachments/assets/f94c1f39-0c5a-4512-836e-84c72fdc1cfb)

```
af=af[((af>=lower_bound)&(af<=upper_bound))]
af
af.dropna()
sns.boxplot(data=af)
sns.scatterplot(data=af)
```
![image](https://github.com/user-attachments/assets/03996e19-6564-4efb-bf66-7a168c04cdb4)

![image](https://github.com/user-attachments/assets/80611f57-96b4-4156-adcd-7d86fa432b59)

```
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of the dtatset is',mean)
print('std. deviation is',std)

threshold=3
outlier=[]
for i in data:
    z=(i-mean)/std
    if z>threshold:
        outlier.append(i)
print('outlier in dataset is',outlier)

import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats

data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
![image](https://github.com/user-attachments/assets/4a94a7a2-99eb-49db-a9a9-d7b727590640)

```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
val=[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,258]

out=[]
def d_o(val):
    ts=3
    m=np.mean(val)
    sd=np.std(val)
    for i in val:
        z=(i-m)/sd
        if np.abs(z)>ts:
            out.append(i)
    return out

op=d_o(val)
op
```
![Screenshot 2025-03-12 224915](https://github.com/user-attachments/assets/7a0746d4-b025-40ac-a79f-e5efba3eef0f)


# Result:
Thus, the Data Cleaning Process is executed Successfully.
