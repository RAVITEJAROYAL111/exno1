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
            <<include your coding and its corressponding output screen shots here>
``
import pandas as pd
import numpy as np
import seaborn as sns
import os
df = pd.read_csv("/content/SAMPLEIDS (2).csv")
df
``
<img width="987" height="816" alt="image" src="https://github.com/user-attachments/assets/7bd793f2-c8a6-4ab7-abdf-c04d1743cc6d" />
```
df.isnull().sum()
```
<img width="372" height="479" alt="image" src="https://github.com/user-attachments/assets/2f83af3f-5424-42f7-b972-b113f3a372b2" />
```
df.isnull().any()
```
<img width="368" height="476" alt="image" src="https://github.com/user-attachments/assets/430515d2-21de-425b-aaf2-24f21f73b299" />
```
df.dropna()
```
<img width="961" height="511" alt="image" src="https://github.com/user-attachments/assets/f2987ca0-1583-4f42-acb4-20444fa756c3" />
```
df.fillna(0)
```
<img width="981" height="812" alt="image" src="https://github.com/user-attachments/assets/ce05b0d5-4d53-438d-a40a-d8a25e705054" />
```
df.fillna(method = 'ffill')
```
<img width="1004" height="830" alt="image" src="https://github.com/user-attachments/assets/24714db4-cbcc-4660-ac0f-62298176f8f3" />
```
df.fillna(method = 'bfill')
```
<img width="948" height="759" alt="image" src="https://github.com/user-attachments/assets/86652948-2f5a-4266-9813-d0102f71b524" />
```
df_dropped = df.dropna()
df_dropped
```
<img width="962" height="522" alt="image" src="https://github.com/user-attachments/assets/06be7136-c34b-4bd7-8165-2b7ade0489bb" />
```
df.fillna({'GENDER':'FEMALE','NAME':'PRIYA','ADDRESS':'POONAMALEE',})
```
<img width="971" height="812" alt="image" src="https://github.com/user-attachments/assets/53320e1d-4e7c-4ad5-b44f-dc2a3bf5e440" />
```
import pandas as pd
ir=pd.read_csv('iris.csv')
ir
```
<img width="626" height="469" alt="image" src="https://github.com/user-attachments/assets/84423fb7-b598-497c-8f76-12a9e8747cf3" />
```
ir.describe()
```
<img width="587" height="329" alt="image" src="https://github.com/user-attachments/assets/db39a357-2114-4c25-8914-164f244f70ab" />
```
import seaborn as sns
sns.boxplot(x='sepal_width,data=ir)
```
<img width="659" height="550" alt="image" src="https://github.com/user-attachments/assets/bef3eb44-0c4b-46f4-8498-aa96864ae519" />
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
<img width="318" height="281" alt="image" src="https://github.com/user-attachments/assets/a9690e40-1962-492c-ba4a-4b05d4517adb" />
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
<img width="616" height="476" alt="image" src="https://github.com/user-attachments/assets/77f42aa6-a22c-4374-936e-5461f519c13b" />
```
sns.boxplot(x='sepal_width',data=delid)
```
<img width="617" height="524" alt="image" src="https://github.com/user-attachments/assets/17b9fde2-8931-4b16-961a-9a69c1ebcce0" />
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("heights.csv")
dataset
```
<img width="189" height="567" alt="image" src="https://github.com/user-attachments/assets/ac464ef5-222d-412e-86da-230967758c1e" />
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr=q3-q1
iqr
```
<img width="392" height="42" alt="image" src="https://github.com/user-attachments/assets/5f53b404-a4f6-4681-99b8-3aa463e5e1b5" />
```
low=q1-1.5*iqr
low
```
<img width="323" height="37" alt="image" src="https://github.com/user-attachments/assets/66b9e2e8-0f18-46cf-be6e-8e232397ba69" />
```
high=q3+1.5*iqr
high
```
<img width="271" height="33" alt="image" src="https://github.com/user-attachments/assets/94ac0ceb-5f7e-4f28-a060-bc81ca8e0753" />
```
df1=df[((df['height']>=low)&(df['height']<=high))]
df1
```
<img width="205" height="490" alt="image" src="https://github.com/user-attachments/assets/bf373bc9-0efe-4d4e-ae9a-fe058d4768ac" />
```
z=np.abs(stats.zscore(df['height']))
z
```
<img width="614" height="90" alt="image" src="https://github.com/user-attachments/assets/94f59818-310b-4024-8318-066b7c7dc00b" />
```
df1=df[z<3]
df1
```
<img width="199" height="526" alt="image" src="https://github.com/user-attachments/assets/ace4a5c6-c9df-45a6-8c0d-552f7c8702bf" />

# Result
          <<include your Result here>>
