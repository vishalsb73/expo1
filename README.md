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
import numpy as np
import pandas as pd
dt=pd.read_csv("SAMPLEIDS.csv")
dt
```
<img width="820" height="646" alt="Screenshot 2025-10-16 210600" src="https://github.com/user-attachments/assets/a06962dc-8671-4a86-9f73-ba6f185bb108" />
```
dt.head()
```
<img width="812" height="201" alt="Screenshot 2025-10-16 210916" src="https://github.com/user-attachments/assets/e2decf51-2be6-4f68-ac88-22acca58ceb4" />
```
dt.tail()
```
<img width="815" height="192" alt="Screenshot 2025-10-16 210946" src="https://github.com/user-attachments/assets/2429c938-4977-476d-a588-2dd3d97744cd" />

```
dt.isnull()
```
<img width="699" height="657" alt="Screenshot 2025-10-16 210957" src="https://github.com/user-attachments/assets/dee5cbef-a8c6-4396-8758-c8893fec7244" />

```
dt.notnull()
```
<img width="702" height="652" alt="Screenshot 2025-10-16 211004" src="https://github.com/user-attachments/assets/91dd3383-5040-4d49-824f-d1d46bfe11c4" />

```
dt.dropna(axis=1)
```
<img width="243" height="641" alt="Screenshot 2025-10-16 211017" src="https://github.com/user-attachments/assets/be532c5c-aab7-45ce-8b19-3e72ee5c7add" />

```
dt.dropna(axis=0)
```
<img width="827" height="431" alt="Screenshot 2025-10-16 211024" src="https://github.com/user-attachments/assets/7ee428d1-dc67-424e-9ce2-03ff5f801d17" />

```
dt.fillna(0)
```
<img width="822" height="652" alt="Screenshot 2025-10-16 211032" src="https://github.com/user-attachments/assets/cd6ea7cd-4c5a-43e7-8988-a54685197724" />

```
dt.fillna(method='ffill')
```
<img width="824" height="647" alt="Screenshot 2025-10-16 211039" src="https://github.com/user-attachments/assets/b5a2baf7-c02c-43b3-a5a5-f50d3cfde246" />

```
ir=pd.read_csv("iris.csv")
ir
```
<img width="490" height="400" alt="Screenshot 2025-10-16 211045" src="https://github.com/user-attachments/assets/6b4d4bb5-d963-4108-a0f9-4147087b0a91" />

```
import seaborn as sns
sns.boxplot(x="sepal_width",data=ir)
```
<img width="649" height="536" alt="Screenshot 2025-10-16 211051" src="https://github.com/user-attachments/assets/383bbb4c-0940-4db9-a1e4-3cd92ef1dfef" />

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="406" height="121" alt="Screenshot 2025-10-16 211056" src="https://github.com/user-attachments/assets/2c0db7c7-079f-4f49-b245-f993e261337d" />

```
rid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid
```
<img width="509" height="403" alt="Screenshot 2025-10-16 211103" src="https://github.com/user-attachments/assets/5144e401-8c48-4d06-8e68-4139144d69b7" />

```
rid=ir[((ir.sepal_width>(q1-1.5*iqr))&(ir.sepal_width<(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="471" height="248" alt="Screenshot 2025-10-16 211108" src="https://github.com/user-attachments/assets/c265ac82-20b8-4741-adb7-2f6ee9bb2b2c" />

```
import scipy.stats as stats
z=np.abs(stats.zscore(ir.sepal_width))
z
```
<img width="529" height="242" alt="Screenshot 2025-10-16 211112" src="https://github.com/user-attachments/assets/13922a7a-f83a-41b4-9554-99f9a7439cf5" />

# Result

Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
