# Marketing Funnel Analysis 📊

## Overview
This project focuses on analyzing a marketing funnel to understand how
users move from visitors to leads and finally to customers. The analysis
helps identify conversion drop-offs, evaluate channel-wise performance,
and suggest data-driven improvements.

This repository is designed to demonstrate practical data analysis
skills using Python and is suitable for portfolio and interview purposes.

---

## Objective
The main objective of this project is to:
- Analyze marketing funnel performance
- Evaluate conversion rates across different marketing channels
- Identify weak points in the funnel
- Provide actionable recommendations to improve lead-to-customer conversion

---

## Dataset
The dataset used in this project contains **500 records** related to
marketing performance.

### Columns Description:
- **date** – Campaign date
- **channel** – Marketing channel (Email, Social Media, Paid Ads, Referral)
- **visitors** – Number of visitors acquired
- **leads** – Number of leads generated
- **customers** – Number of customers converted
- **ad_spend** – Advertising spend for the channel

Dataset file:📂 **Dataset:**  
[Download marketing_funnel_500_rows.csv](marketing_funnel_500_rows.csv)

- **Task03.ipynb** → Main analysis notebook
- **marketing_funnel_500_rows.csv** → Dataset used for analysis
- **README.md** → Project documentation

---

## Tools & Technologies Used
- Python
- Pandas
- NumPy
- Matplotlib
- seaborn
- plotly
- Jupyter Notebook 

---
## Data Exploration, Cleaning, and Feature Engineering

### Data Understanding
The dataset was first explored to understand its structure, data types, summary statistics, and the presence of missing values. This step helps identify potential data quality issues before cleaning and analysis.

python
df.info()
df.describe()
df.isnull().sum()

---
### Handling Missing Values
Missing values were handled carefully to preserve data integrity. The numerical column ad_spend was filled using the median to minimize the impact of outliers, while missing values in the categorical channel column were filled using the most frequently occurring category.
Copy code
Python
df['ad_spend'].fillna(df['ad_spend'].median(), inplace=True)
df['channel'].fillna(df['channel'].mode()[0], inplace=True)

---

### Removing Duplicates and Invalid Records
Duplicate rows were removed to prevent repeated observations from affecting the analysis. Additionally, invalid records were filtered out by ensuring that visitor counts were greater than zero and that lead and customer values were non-negative, maintaining realistic funnel behavior.
Copy code
Python
df.drop_duplicates(inplace=True)
df = df[(df['visitors'] > 0) & (df['leads'] >= 0) & (df['customers'] >= 0)]

---

### Feature Engineering
After cleaning the dataset, new performance metrics were created to support funnel analysis. Visitor-to-lead conversion rate measures top-of-funnel efficiency, lead-to-customer conversion rate evaluates conversion quality, and cost per lead helps assess marketing cost efficiency.
Copy code
Python
df['VLC'] = (df['leads'] / df['visitors']) * 100
df['LCC'] = (df['customers'] / df['leads']) * 100
df['CPL'] = df['ad_spend'] / df['leads']
These steps prepared the dataset for accurate channel-wise analysis and visualization, ensuring reliable insights into marketing funnel performance.

---

## Analysis Performed
The following analysis steps were performed in the notebook:

1. Data loading and inspection
2. Data cleaning (handling zero and missing values)
3. Funnel metric calculations:
   - Visitor to Lead Conversion Rate
   - Lead to Customer Conversion Rate
4. Channel-wise performance analysis
5. Visualization of conversion metrics
6. Business insights and interpretation

---

## Key Metrics
- **Visitor to Lead Conversion Rate (V → L)**  
  Measures how effectively visitors are converted into leads.

- **Lead to Customer Conversion Rate (L → C)**  
  Measures how efficiently leads are converted into customers.

- **Cost Per Lead (CPL)**  
  Indicates the cost required to acquire one lead.

---

## Key Insights
- Email and Referral channels show higher conversion efficiency.
- Paid Ads generate high traffic but lower lead-to-customer conversion.
- Higher ad spend does not always guarantee better customer conversion.
- Funnel drop-offs are most significant between the lead and customer stages.

---

## Recommendations
- Optimize landing pages for Paid Ads campaigns.
- Focus budget allocation on high-performing channels like Email and Referral.
- Improve lead nurturing strategies to reduce funnel drop-offs.
- Prioritize conversion optimization over increasing ad spend.

---

## How to Run the Project
1. Clone the repository:
   ```bash
   git clone https://github.com/rajpatil56/FL.git
