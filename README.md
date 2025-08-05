from google.colab import files
uploaded = files.upload()
import zipfile
with zipfile.ZipFile("archive (1).zip", 'r') as zip_ref:
zip_ref.extractall("dataset")
import os
os.listdir("dataset")
['Mall_Customers.csv']
CustomerID Gender Age Annual Income (k$) Spending Score (1-100)
0 1 Male 19 15 39
1 2 Male 21 15 81
2 3 Female 20 16 6
3 4 Female 23 16 77
4 5 Female 31 17 40
import pandas as pd
df = pd.read_csv("dataset/Mall_Customers.csv")
df.head()
print("Shape:", df.shape)
print("Columns:", df.columns)
print("\nMissing values:\n", df.isnull().sum())
print("\nDuplicates:", df.duplicated().sum())
df.columns = df.columns.str.strip().str.lower().str.replace(' ', '_')
if 'gender' in df.columns:
df['gender'] = df['gender'].str.lower().str.strip()
df = df.drop_duplicates()
print(df.dtypes)
df.to_csv("cleaned_mall_data.csv", index=False)
Shape: (200, 5)
Columns: Index(['customerid', 'gender', 'age', 'annual_income_(k$)',
 'spending_score_(1-100)'],
 dtype='object')
Missing values:
 customerid 0
gender 0
age 0
annual_income_(k$) 0
spending_score_(1-100) 0
dtype: int64
Duplicates: 0
customerid int64
gender object
age int64
annual_income_(k$) int64
spending_score_(1-100) int64
dtype: object
05/08/2025, 17:35 Untitled7.ipynb - Colab
https://colab.research.google.com/drive/1BoPX2gvfU9LRXwMPrXdgSgRnUAYSaH8e#scrollTo=vOAkgP1CEdA2&printMode=true 1/2
from google.colab import files
files.download("cleaned_mall_data.csv")


