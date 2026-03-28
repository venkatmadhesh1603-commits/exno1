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
# Step 1: Import Required Libraries

import pandas as pd import numpy as np from scipy import stats import seaborn as sns import matplotlib.pyplot as plt

# Step 2: Read the Dataset

df2 = pd.read_csv('Data_set.csv') df2.head()

# Step 3: Dataset Information

df2.info() df2.describe()

# Step 4: Handling Missing Values

Check Null Values
df2.isnull() df2.isnull().sum()


Fill Missing Values with 0
df2_fill_0 = df2.fillna(0) df2_fill_0


Forward Fill
df2_ffill = df2.ffill() df2_ffill


Backward Fill
df2_bfill = df2.bfill() df2_bfill


Fill with Mean (Numerical Column Example)
df2['watchers'] = df2['watchers'].fillna(df2['watchers'].mean()) df2


Drop Missing Values
df2_dropna = df2.dropna() df2_dropna


# Step 5: Save Cleaned Data

df2_dropna.to_csv('clean_data_2.csv', index=False)

OUTLIER DETECTION

# Step 6: IQR Method (Using Iris Dataset)
ir = pd.read_csv('Data_set.csv') ir.head() ir.info() ir.describe()

Boxplot for Outlier Detection

sns.boxplot(x=ir['watchers']) plt.show()

Calculate IQR

Q1 = ir['watchers'].quantile(0.25) Q3 = ir['watchers'].quantile(0.75) IQR = Q3 - Q1 print("IQR:", IQR)

Detect Outliers

outliers_iqr = ir[ (ir['watchers'] < (Q1 - 1.5 * IQR)) | (ir['watchers'] > (Q3 + 1.5 * IQR)) ] outliers_iqr

Remove Outliers

ir_cleaned = ir[ ~((ir['watchers'] < (Q1 - 1.5 * IQR)) | (ir['watchers'] > (Q3 + 1.5 * IQR))) ] ir_cleaned

# Step 7: Z-Score Method

data = [1,12,15,18,21,24,27,30,33,36,39,42,45,48,51, 54,57,60,63,66,69,72,75,78,81,84,87,90,93] df2_z = pd.DataFrame(data, columns=['values']) df2_z

Calculate Z-Scores

z_scores = np.abs(stats.zscore(df2_z)) z_scores

Detect Outliers

threshold = 3 outliers_z = df2_z[z_scores > threshold] print("Outliers:") outliers_z

Remove Outliers

df2_z_cleaned = df2_z[z_scores <= threshold] df2_z_cleaned

# Output

<img width="788" height="714" alt="546025960-c25b916a-4eb5-4ef2-9780-ef585fed9160" src="https://github.com/user-attachments/assets/eeb11875-d06b-4e06-8164-d500fc454542" />
<img width="386" height="228" alt="546026046-78f5fbb4-6e05-4d15-9ab4-df40117b1440" src="https://github.com/user-attachments/assets/895c7e47-13d3-422c-af9a-d391cf2bb849" />
<img width="1029" height="387" alt="546026098-b4296922-722e-49fa-b797-e4279db2e032" src="https://github.com/user-attachments/assets/17349274-61e8-4494-b5cf-7b5c8bb05b95" />
<img width="1031" height="803" alt="546026146-cd4bd119-0d28-4f96-8bc7-866f4312844b" src="https://github.com/user-attachments/assets/f992356e-c2aa-4d86-8aba-f7fbcb462f2d" />
<img width="563" height="823" alt="546026238-899d73d9-d393-46be-9386-b21334888e17" src="https://github.com/user-attachments/assets/539b72c6-6eec-4573-9129-05144163c521" />
<img width="433" height="811" alt="546026284-2b4cf545-e927-40b1-acce-12d70a270c04" src="https://github.com/user-attachments/assets/ab127c3d-7653-4fed-a63b-d96f98025d38" />


# Result


     Thus , the data cleaning process is completed successfully ..
