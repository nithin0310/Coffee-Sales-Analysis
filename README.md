# Coffee Sales Analysis

## Introduction
Coffee vending machines generate valuable sales data that can reveal customer purchasing behavior, peak sales periods, and revenue trends. This project leverages **Exploratory Data Analysis (EDA)** to analyze coffee sales data, providing insights to optimize stock management, pricing, and marketing strategies.

## Problem Statement
Many businesses operating coffee vending machines lack **data-driven insights** into customer behavior and sales performance. This results in inefficiencies such as:
- Overstocking or understocking popular coffee types.
- Missed opportunities for targeted promotions and pricing strategies.
- Inability to identify demand fluctuations across different times of the day, week, and month.

This project analyzes historical transaction data to uncover trends in:
1. Coffee type preferences and sales volume.
2. Peak sales hours and days for better inventory planning.
3. Impact of payment methods (cash vs. card) on revenue.
4. Monthly revenue trends and seasonal demand shifts.

## Dataset
- The dataset contains **coffee sales records** from a vending machine, capturing details like **date, time, coffee type, payment method, and amount spent**.
- Data spans from **March 2024 to the present**, updated regularly.

## Tools Used
- **Python** (Pandas, Matplotlib, Seaborn, NumPy)
- **Google Colab**

## Code Implementation
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
data = pd.read_csv('coffee_sales.csv')

# Rename columns for clarity
data = data.rename(columns={'datetime': 'timestamp', 'cash_type': 'payment_mode', 'money': 'amount'})

# Convert to datetime format
data['order_date'] = pd.to_datetime(data['date'])
data['timestamp'] = pd.to_datetime(data['timestamp'])

# Extract time-based insights
data['hour'] = data['timestamp'].dt.hour
data['day_of_week'] = data['order_date'].dt.day_name()

# Sales trend by hour
plt.figure(figsize=(10, 5))
sns.histplot(data['hour'], bins=24, color='brown', edgecolor='black')
plt.xlabel("Hour of Day")
plt.ylabel("Orders Count")
plt.title("Hourly Coffee Demand")
plt.grid(axis='y', linestyle='--', alpha=0.6)
plt.show()

# Sales distribution by coffee type
coffee_sales = data['coffee_name'].value_counts()
plt.figure(figsize=(10, 5))
coffee_sales.plot(kind='bar', color='saddlebrown')
plt.xlabel("Coffee Type")
plt.ylabel("Sales Volume")
plt.title("Coffee Sales by Type")
plt.xticks(rotation=45, ha='right')
plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.show()
```

## Key Insights
### **1. Payment Method Trends**
- **Card payments** dominate transactions, but cash is still widely used.
- Customers using **card payments tend to spend more**, suggesting upselling potential.
- A **discount program** for digital payments could increase cashless adoption.

### **2. Coffee Type Preferences**
- **Espresso and cappuccino** are the most popular choices.
- Seasonal or **limited-edition coffees have niche demand**.
- Offering **combo deals on less popular coffee types** may increase sales.

### **3. Sales Patterns by Time & Day**
- **Morning hours (8-10 AM)** see the highest coffee sales.
- A **smaller evening peak** suggests coffee is also a social drink.
- **Weekend sales are higher**, likely due to leisure outings.

### **4. Revenue & Seasonal Trends**
- **Revenue fluctuates seasonally**, with peaks in colder months.
- **Targeted promotions during slow months** could improve revenue stability.
- **Loyalty programs** may encourage repeat customers.

## Conclusion
By leveraging **data analytics**, businesses can:
- Improve **inventory planning** based on sales patterns.
- Optimize **pricing and promotions** for slow periods.
- Enhance **customer experience** by ensuring availability of high-demand products.

## How to Run the Notebook
1. Open the project in **Google Colab**.
2. Upload the dataset (`coffee_sales.csv`).
3. Run the Python cells to visualize sales trends.

---
This project provides **actionable insights** for optimizing vending machine sales performance using data-driven decisions.
