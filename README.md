# jai-bisht
🧠 Step 1: Import Libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
📂 Step 2: Load Dataset
df = pd.read_csv("retail_sales.csv")
df.head()
🔍 Step 3: Data Understanding
df.info()
df.describe()
df.isnull().sum()
Key Observation:
No major missing values
Data contains both numerical and categorical variables
Suitable for EDA and visualization
📊 Step 4: Sales Distribution
plt.figure()
sns.histplot(df['Sales'], bins=30)
plt.title("Sales Distribution")
plt.show()

👉 Insight: Most sales are in lower range, few high-value transactions exist.

📈 Step 5: Category-wise Sales
category_sales = df.groupby("Category")["Sales"].sum().reset_index()

plt.figure()
sns.barplot(x="Category", y="Sales", data=category_sales)
plt.title("Sales by Category")
plt.show()

👉 Insight:

One category dominates sales
Other categories contribute moderately
💰 Step 6: Profit Analysis
profit_by_category = df.groupby("Category")["Profit"].sum().reset_index()

plt.figure()
sns.barplot(x="Category", y="Profit", data=profit_by_category)
plt.title("Profit by Category")
plt.show()

👉 Insight:

High sales ≠ high profit always
Some categories generate low or negative profit
🔥 Step 7: Correlation Analysis
corr = df[['Sales','Profit','Quantity']].corr()

plt.figure()
sns.heatmap(corr, annot=True, cmap="coolwarm")
plt.title("Correlation Matrix")
plt.show()

👉 Insight:

Sales and Profit have moderate correlation
Quantity has weaker impact on profit
🌍 Step 8: Region-wise Performance
region_sales = df.groupby("Region")["Sales"].sum().reset_index()

plt.figure()
sns.barplot(x="Region", y="Sales", data=region_sales)
plt.title("Region-wise Sales")
plt.show()

👉 Insight:

Some regions outperform others significantly
Indicates geographic demand differences
