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
```
import pandas as pd 
df = pd.read_csv("SAMPLEIDS (1).csv")
df
```
![image](https://github.com/user-attachments/assets/d9c2cff0-19f1-4b13-8e02-8bb11e831195)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/2ebad94c-15f8-41e6-a8d5-31351503d803)
```
df.isnull().any()
```
![image](https://github.com/user-attachments/assets/8e06cb51-e171-4100-959b-019af58beff5)
```
df.dropna()
```
![image](https://github.com/user-attachments/assets/e81112eb-c57f-410e-af17-48bdd9cb35fa)
```
df.fillna(0)
```
![image](https://github.com/user-attachments/assets/fca2ef32-5a42-4ce6-9f24-8d559de8d560)
```
df.fillna(method = 'ffill')
```
![image](https://github.com/user-attachments/assets/b9406cb3-d104-43ce-8620-81c54b3cae47)
```
df.fillna(method = 'bfill')
```
![image](https://github.com/user-attachments/assets/f6322896-0092-483d-8154-e52948b26b5c)
```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
```
![image](https://github.com/user-attachments/assets/a5775f6d-05c4-4b3d-96a3-d1ec35abde55)

## IQR(Inter Quartile Range)
```
import pandas as pd
ris = pd.read_csv("iris (1).csv")
ris
```
![image](https://github.com/user-attachments/assets/30df7952-5c43-45b2-b359-c5faaa54ea8e)
```
ris.describe()
```
![image](https://github.com/user-attachments/assets/5b56f99c-f18b-4852-91fd-3431e404a162)
```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ris)
```
![image](https://github.com/user-attachments/assets/2ecd860e-c95e-45d7-af0c-0a51b667edab)
```
c1=ris.sepal_width.quantile(0.25)
c3=ris.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/user-attachments/assets/a2d79a7c-9a9c-4e5f-b6b2-9ea0ddd8006d)
```
rid=ris[((ris.sepal_width<(c1-1.5*iq))|(ris.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/user-attachments/assets/762ef0bd-ee23-4286-8d7a-3f7591cca04b)
```
 delid=ris[~((ris.sepal_width<(c1-1.5*iq))|(ris.sepal_width>(c3+1.5*iq)))]
 delid
```
![image](https://github.com/user-attachments/assets/b90ff9e2-c635-48a1-b699-de5afaea40d8)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/user-attachments/assets/4c90c378-052c-4237-b0ff-b765bc330da1)

## Z SCORE
```
import matplotlib.pyplot as plt 
import pandas as pd
import numpy as np
import scipy.stats as stats
ds = pd.read_csv("heights.csv")
ds
```
![image](https://github.com/user-attachments/assets/588170df-1b7d-4b83-9ba2-aa97e63543be)
```
q1 = ds['height'].quantile(0.25)
q2 = ds['height'].quantile(0.5)
q3 = ds['height'].quantile(0.75)
iqr =q3 - q1
iqr
```
![image](https://github.com/user-attachments/assets/723762db-855b-4d69-a733-9ca7ac40826c)
```
low = q1- 1.5*iqr
low
high = q3+ 1.5*iqr
high
```
![image](https://github.com/user-attachments/assets/b9d60fd5-5cc0-4938-ad6c-d75cadcbd868)
```
 ds1 = ds[((ds['height'] >=low)& (ds['height'] <=high))]
 ds1
```
![image](https://github.com/user-attachments/assets/056b73ca-d69e-4e83-83b9-bcdb8eb504e8)
```
import numpy as np
import scipy.stats as stats
z = np.abs(stats.zscore(ds['height']))
z
```
![image](https://github.com/user-attachments/assets/2aebde52-27a6-449a-8570-864349bcba0a)
```
ds1 = ds[z<3]
ds1
```
![image](https://github.com/user-attachments/assets/4b2e770b-b5ad-4a4a-8f66-57d008fa3df6)


# Result
   Thus we have cleaned the data and removed the outliers by detection using IQR and Z -score method.
