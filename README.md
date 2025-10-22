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
import numpy as np
df=pd.read_csv("SAMPLEIDS.csv")
df
```

<img width="902" height="705" alt="image" src="https://github.com/user-attachments/assets/f10e9031-cf51-4baf-beb4-902d78af2a5f" />

```
df.head(4)
```

<img width="923" height="192" alt="image" src="https://github.com/user-attachments/assets/f5e3cfc5-8aba-43d0-9929-10bf64610b56" />


```
df.tail(7)
```

<img width="933" height="289" alt="image" src="https://github.com/user-attachments/assets/7fcdc6e1-1306-4ea1-b082-97e76efbdaaa" />


```
df.isnull()
```

<img width="823" height="739" alt="image" src="https://github.com/user-attachments/assets/d795e077-26d9-41e3-a922-0915e47fbfee" />


```
df.notnull()
```

<img width="818" height="749" alt="image" src="https://github.com/user-attachments/assets/993d1d70-38b3-4970-b559-cf6e2dba4875" />


```
df.isnull().sum()
```

<img width="265" height="302" alt="image" src="https://github.com/user-attachments/assets/b7814b46-5699-449e-85e4-a871c8cd7a71" />


```
df.isnull().any()
```

<img width="259" height="294" alt="image" src="https://github.com/user-attachments/assets/1bb47931-8525-4039-8a59-fa5c37365e9f" />


```
df.dropna(axis=1)
```

<img width="393" height="728" alt="image" src="https://github.com/user-attachments/assets/23c6d470-79cd-40fc-97aa-15136ae2ef5e" />


```
df.dropna(axis=0)
```

<img width="924" height="477" alt="image" src="https://github.com/user-attachments/assets/b567cf45-26e2-4068-9445-2db5811b751e" />


```
df.fillna(0)
```

<img width="951" height="729" alt="image" src="https://github.com/user-attachments/assets/6ddf78e4-ff28-4109-904f-6ed7c64df97a" />


```
df.fillna(method="ffill")
```

<img width="929" height="726" alt="image" src="https://github.com/user-attachments/assets/73631f07-026d-4b2d-9e0e-64bccf8d5e82" />


```
df.bfill()
```

<img width="937" height="747" alt="image" src="https://github.com/user-attachments/assets/042a4658-c67f-4b93-a815-cbaf282431a5" />


```
df.fillna({'REGNO':0, 'NAME':'PRAVEEN'})
```

<img width="942" height="750" alt="image" src="https://github.com/user-attachments/assets/48c6cb23-f724-4cf9-9934-e92459a90713" />


```
ir=pd.read_csv("iris.csv")
ir
```

<img width="612" height="458" alt="image" src="https://github.com/user-attachments/assets/7493c723-19ab-4172-a195-3ea37e21b46f" />


```
ir.describe()
```

<img width="522" height="322" alt="image" src="https://github.com/user-attachments/assets/6b8b3898-ffe0-4010-9300-194f401b30f6" />


```
import seaborn as sns
sns.boxplot(x="sepal_width",data=ir)
```

<img width="709" height="597" alt="image" src="https://github.com/user-attachments/assets/6c274161-186e-4c83-9937-f53ec29a8682" />


```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```

<img width="112" height="41" alt="image" src="https://github.com/user-attachments/assets/7e8d990c-c110-4a60-8e1e-58e32908a555" />


```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```

<img width="376" height="137" alt="image" src="https://github.com/user-attachments/assets/e47afc50-cc18-4c86-b34c-c9e8d07e4762" />


```
rid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid
```

<img width="607" height="476" alt="image" src="https://github.com/user-attachments/assets/55353526-fd27-46ef-bfe7-05e01daf5d41" />


```
rid=ir[((ir.sepal_width>(q1-1.5*iqr))&(ir.sepal_width<(q3+1.5*iqr)))]
rid['sepal_width']
```

<img width="480" height="276" alt="image" src="https://github.com/user-attachments/assets/e3fa7d0f-28f5-4d81-b8c7-907d9c0e8dfe" />

```
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir.sepal_width))
z
```

<img width="480" height="274" alt="image" src="https://github.com/user-attachments/assets/71643d8d-9c15-4ac3-988c-c8ee7ae87448" />

# Result
Thus we have cleaned the data and removed the outliers by detectionusing IQR and Z-score method
