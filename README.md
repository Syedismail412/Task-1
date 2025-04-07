# Data Cleaning: Marketing Campaign Dataset

## Objective
To clean and prepare a raw marketing dataset by:
- Removing duplicates
- Handling null values
- Fixing inconsistent data formats
- Converting string dates to proper datetime objects

## Dataset
The dataset used is `marketing_campaign.csv`, which includes customer demographics, purchase history, and campaign responses.

## Cleaning Steps

1. **Load Data**
```python
df = pd.read_csv('marketing_campaign.csv', sep='\\t')
Remove Duplicates

python
Copy
Edit
df = df.drop_duplicates()
Handle Null Values

python
Copy
Edit
df = df.dropna()
Standardize Text Columns

python
Copy
Edit
str_cols = df.select_dtypes(include='object').columns
for col in str_cols:
    df[col] = df[col].str.strip().str.lower()
Convert Date Column

python
Copy
Edit
df.rename(columns=lambda x: x.strip(), inplace=True)
df['Dt_Customer'] = pd.to_datetime(df['Dt_Customer'], format='%d-%m-%Y', errors='coerce')
df = df.dropna(subset=['Dt_Customer'])
Reset Index

python
Copy
Edit
df.reset_index(drop=True, inplace=True)
Save Cleaned File

python
Copy
Edit
df.to_csv('cleaned_marketing_campaign.csv', index=False)
Output
cleaned_marketing_campaign.csv

Requirements
Python 3.x

pandas (pip install pandas)

Author
syed ismail""

Save to READ
