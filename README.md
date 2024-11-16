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

## DATA CLEANING 

## DATA CLEANING 
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS (1).csv")
df
```
![Screenshot (16)](https://github.com/user-attachments/assets/d0457ac5-12c0-4c25-ae22-92e67a06c6f5)

```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/7fe8c0ed-3f49-4aa2-9aa6-d3a9e2f49012)

```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/6cba4a8a-bd9c-47d4-9dc1-c2829de2e86d)

```
df.dropna()
```
![image](https://github.com/user-attachments/assets/3825c336-549e-440d-ad01-939486d5fe0d)

```
df.fillna(0)
```
![Screenshot (17)](https://github.com/user-attachments/assets/e3ae46b7-08c2-413d-aa64-d6e73de859f3)

```
df.fillna(method = 'ffill')
```
![Screenshot (18)](https://github.com/user-attachments/assets/ebb6772e-328d-4328-8063-30e4962b091a)

```
df.fillna(method = 'bfill')
```
![Screenshot (19)](https://github.com/user-attachments/assets/c5340180-8921-4cbf-a35a-4fd46e1b7e8d)

```
df_dropped = df.dropna()
df_dropped
```
![image](https://github.com/user-attachments/assets/c83fa33d-468e-4777-a58a-95377e500853)

```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![Screenshot (20)](https://github.com/user-attachments/assets/234b74ba-01e4-4e8a-954c-026e7da5c5ab)

## IQR (INTER QUARTILE RANGE) 

```
import pandas as pd
import seaborn as sns 
import numpy as np
ir=pd.read_csv('/content/iris (1).csv')
ir
```
![image](https://github.com/user-attachments/assets/60903fc3-7c4d-4c34-b986-25e5944d4711)

```
ir.describe()
```
![image](https://github.com/user-attachments/assets/7a105c44-e01d-4b97-9cd1-a5426e8d4679)

```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/user-attachments/assets/1c4bfdcd-6ed9-42d3-abd4-c8976f30c562)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/bb1c2d0b-9ca1-4777-8d3d-903da6ab150c)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/b15667e2-87b0-4f68-9254-9b8a0029ba00)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/user-attachments/assets/5c8dd841-1725-4cce-882f-57fcecd591f1)

```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/9d39e3ae-bcaa-44ea-80ec-54494804ec52)

## Z - SCORE 

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights (1).csv")
dataset
```
![image](https://github.com/user-attachments/assets/cea2b511-c333-4f08-aa96-702cf9453be5)

```
df = pd.read_csv("/content/heights (1).csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/96e15df5-0854-4f69-b009-94462c3bebaf)

```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/user-attachments/assets/727d10e0-7cf2-485e-936c-b2553da7e32a)

```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/998c9bc0-4b8b-44c4-9a42-fb9d06ea26eb)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/user-attachments/assets/8e09beeb-f485-4268-a6ba-89ce1c16a5de)

```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/user-attachments/assets/5e92e873-97e8-4e35-af9c-d2ffb508d21b)

```
df1 = df[z<3]
df1
```
![image](https://github.com/user-attachments/assets/6d86f590-3b88-416a-ba47-fa739cc5d548)

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
