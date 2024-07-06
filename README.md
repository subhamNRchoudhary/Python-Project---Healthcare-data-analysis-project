Python-Project---Healthcare-data-analysis-project




## Project Overview
This project involves analyzing a healthcare dataset to uncover patterns and trends related to medical conditions, billing amounts, and hospital admissions. The analysis uses Python libraries such as NumPy, Pandas, Matplotlib, and Seaborn.

## Dataset
The dataset used for this project can be found [here](https://docs.google.com/spreadsheets/d/15ylaUMDgcQSH3dR9aMlwoBwAJDmYkO12/edit?usp=sharing).

## Analysis Steps
1. **Load the dataset**
2. **Clean the data**
3. **Fill missing values with appropriate methods**
4. **Analyze average billing amounts**
5. **Analyze blood type distribution**
6. **Analyze gender distribution**
7. **Analyze medical conditions**
8. **Analyze insurance coverage amounts**
9. **Analyze monthly admissions**
10. **Analyze medical conditions by gender**

## Libraries Used
- NumPy
- Pandas
- Matplotlib
- Seaborn

## How to Run the Analysis
1. Clone the repository
2. Install the required libraries using `pip install -r requirements.txt`
3. Run the Jupyter notebook `notebooks/healthcare_data_analysis.ipynb`



### 2. healthcare_data_analysis.ipynb


# Import necessary libraries
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
url = "https://docs.google.com/spreadsheets/d/15ylaUMDgcQSH3dR9aMlwoBwAJDmYkO12/edit?usp=sharing"
data = pd.read_csv(url)

# Display the first few rows of the dataset
data.head()

# Data Cleaning
# Handle missing values
data.fillna(method='ffill', inplace=True)

# Analysis: Average Billing Amounts
average_billing = data['Billing Amount'].mean()
print(f'Average Billing Amount: {average_billing}')

# Visualization: Blood Type Distribution
plt.figure(figsize=(10, 6))
sns.countplot(data['Blood Type'])
plt.title('Blood Type Distribution')
plt.savefig('../images/blood_type_distribution.png')
plt.show()

# Visualization: Gender Distribution
plt.figure(figsize=(10, 6))
sns.countplot(data['Gender'])
plt.title('Gender Distribution')
plt.savefig('../images/gender_distribution.png')
plt.show()

# Analysis: Medical Conditions
conditions = data['Medical Condition'].value_counts()
plt.figure(figsize=(12, 8))
sns.barplot(x=conditions.index, y=conditions.values)
plt.title('Medical Conditions')
plt.xticks(rotation=90)
plt.savefig('../images/medical_conditions.png')
plt.show()

# Analysis: Average Amount Provided by Insurance
average_insurance = data['Insurance Amount'].mean()
print(f'Average Amount Provided by Insurance: {average_insurance}')

# Visualization: Monthly Admissions
monthly_admissions = data.groupby('Month')['Admissions'].sum()
monthly_admissions.plot(kind='bar', figsize=(12, 8))
plt.title('Monthly Admissions')
plt.xlabel('Month')
plt.ylabel('Number of Admissions')
plt.savefig('../images/monthly_admissions.png')
plt.show()

# Analysis: Medical Conditions by Gender
conditions_gender = data.groupby(['Gender', 'Medical Condition']).size().unstack()
conditions_gender.plot(kind='bar', stacked=True, figsize=(12, 8))
plt.title('Medical Conditions by Gender')
plt.savefig('../images/medical_conditions_by_gender.png')
plt.show()
```

### 3. requirements.txt

```plaintext
numpy
pandas
matplotlib
seaborn
```

