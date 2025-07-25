# Uber-Fare-Data-Insights

---

## 🧾 Methodology

### 1. Data Understanding and Preparation
- **📥 Downloaded Dataset**: [Uber Fares on Kaggle](https://www.kaggle.com/)
- **🔍 Performed EDA** using Python (Pandas & Matplotlib)
- **🧹 Cleaned Data**: Handled missing values, removed duplicates
- **📤 Exported CSV** for Power BI usage

📸 _Screenshot of Data Loading in Python_  
```python
from google.colab import drive
drive.mount('/content/drive')
import pandas as pd
uber_df=pd.read_csv('/content/drive/MyDrive/archive/uber.csv',low_memory=False)
```
<img width="756" height="255" alt="image" src="https://github.com/user-attachments/assets/8110338b-a8c6-452e-b3da-a323f6e5f800" />

---

### 2. Exploratory Data Analysis (EDA)
- Summary statistics (mean, median, std. dev.)
- Fare distribution and outlier detection
- Correlations: fare vs. distance, time of day, etc.

📸 _Sample EDA Charts_  
```python
print(uber_df['fare_amount'].mean())
print(uber_df['fare_amount'].median())
print(uber_df['fare_amount'].mode())
print(uber_df['fare_amount'].std())
print(uber_df['fare_amount'].quantile([0.25, 0.5, 0.75]))

# Outlier check
import seaborn as sns
import matplotlib.pyplot as plt

sns.boxplot(uber_df['fare_amount'])
plt.show()
```
<img width="1533" height="622" alt="image" src="https://github.com/user-attachments/assets/7428e1d5-c51f-4141-ae0d-2f1f2038f7fa" />
```python
plt.hist(uber_df['fare_amount'], bins=50)
plt.title('Fare Amount Distribution')
plt.xlabel('Fare')
plt.ylabel('Frequency')
plt.show()
```
<img width="1543" height="454" alt="image" src="https://github.com/user-attachments/assets/80f732eb-59d4-4c7a-8500-ac5a32454570" />

---

### 3. Feature Engineering
- Extracted features: `Hour`, `Day`, `Month`
- Added `Day of Week`, `Peak/Off-Peak` labels
- Encoded categorical variables

📸 _Feature Creation Code & Output_  
```python
uber_df['pickup_datetime'] = pd.to_datetime(uber_df['pickup_datetime'])
uber_df['hour'] = uber_df['pickup_datetime'].dt.hour
uber_df['day'] = uber_df['pickup_datetime'].dt.day
uber_df['month'] = uber_df['pickup_datetime'].dt.month
uber_df['day_of_week'] = uber_df['pickup_datetime'].dt.day_name()
# Make sure the column is in datetime format
uber_df['pickup_datetime'] = pd.to_datetime(uber_df['pickup_datetime'])

# Extract hour, day, and month
uber_df['hour'] = uber_df['pickup_datetime'].dt.hour
uber_df['day'] = uber_df['pickup_datetime'].dt.day
uber_df['month'] = uber_df['pickup_datetime'].dt.month
```
<img width="1530" height="173" alt="image" src="https://github.com/user-attachments/assets/59382327-bc30-45fd-99db-2ce8b94529f5" />

---

### 4. Power BI Analysis
- Imported cleaned dataset into Power BI
- Created dynamic visualizations:
  - Fare trends by hour/day/month
  - Peak ride periods
  - Ride duration comparisons

📸 _Power BI Visualizations_  
---

### 5. Dashboard Design
- Interactive filters (Time, Fare Ranges, etc.)
- Visuals used:
  - Bar charts, Boxplots, Time series graphs
  - Map for ride locations (if coordinates available)

📸 _Final Dashboard Screenshot_  
<img width="991" height="583" alt="image" src="https://github.com/user-attachments/assets/1ae73253-d885-43e7-b795-ecd13c3dc3d1" />
<img width="940" height="569" alt="image" src="https://github.com/user-attachments/assets/71a836ed-c28b-4e36-b5b1-bb04f02681ea" />

---

## 📊 Key Insights

- Highest fares occur during late-night hours and weekends
- Longer distances correlate with higher fares but not linearly
- Peak activity between 6 PM – 9 PM across weekdays
- Seasonal variations influence fare averages

---

## 📑 Final Report

Choose one:
- ✅ [ ] GitHub Markdown Report (`report/Uber_Fares_Report.md`)

Includes:
- Dataset Summary  
- Cleaning & Processing Steps  
- Feature Engineering Explained  
- Key Visuals & Insights  
- Recommendations for Uber

---

## ✅ Submission Checklist

- [x] `.pbix` Dashboard uploaded
- [x] Cleaned `.csv` files included
- [x] Final report (MD)
- [x] GitHub repo publicly accessible
- [x] Email with link sent before deadline

---
