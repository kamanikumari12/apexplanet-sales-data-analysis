# 📊 apexplanet-sales-data-analysis

## 🎯 Project Overview
This project performs Exploratory Data Analysis (EDA) and data preprocessing on the **ApexPlanet Sales Dataset**. The goal is to clean raw transaction logs, resolve data quality issues, and prepare structured sales metrics for downstream business intelligence and reporting.

* **Dataset Source:** `ApexPlanet_DataAnalytics_Dataset.xlsx`
* **Total Records:** 1,000 sales transactions
* **Key Deliverables:** Cleaned Dataset, Data Quality Report, Data Analysis Scripts
* **Tech Stack:**
  -Python 3.10+
  -Pandas
  -NumPy
  -Jupyter Notebook / VS Code
  -Git
## 📖 Data Dictionary

| Column Name | Data Type | Null Count | Description | Example / Range Values |
| :--- | :--- | :--- | :--- | :--- |
| `Order_ID` | String / Object | 0 | Unique identifier for each transaction | `ORD100002` |
| `Order_Date` | Date (YYYY-MM-DD) | 0 | Date when the order was placed | `2025-02-25` |
| `Customer_ID` | String / Object | 0 | Unique identifier for each customer | `CUST5529` |
| `Customer_Name` | String / Object | 0 | Customer profile label | `Customer_227` |
| `Age` | Float / Integer | 20 | Customer age in years | `30` (Range: 18 – 65) |
| `Gender` | String / Object | 0 | Customer gender classification | `Female`, `Male` |
| `City` | String / Object | 13 | Delivery / customer city | `Bengaluru`, `Kolkata`, `Hyderabad` |
| `Product` | String / Object | 0 | Product item purchased | `Rice`, `Book`, `Mobile` |
| `Category` | String / Object | 0 | Broad category of the product | `Grocery`, `Education`, `Electronics` |
| `Quantity` | Integer | 0 | Units purchased in the transaction | `7` (Range: 1 – 10) |
| `Unit_Price` | Float | 0 | Price per unit item in INR | `2829.77` |
| `Total_Sales` | Float | 0 | Total bill amount (`Quantity` × `Unit_Price`) | `19808.39` |


## 🛠️ Data Quality Issues & How They Were Fixed

During initial inspection, several data quality issues were identified and resolved:
1. Missing Values (Nulls)
* **Issue:** 
  * `Age` column had **20 missing entries** (~2.0%).
  * `City` column had **13 missing entries** (~1.3%).
* **Impact:** Incomplete demographic and geographic analytics.
* **Fix Applied:** 
  * Imputed missing `Age` values using median age.
  * Replaced missing `City` values with `"Unknown"` or mode city per region.

2. Duplicate Records
* **Issue:** **8 duplicate `Order_ID` records** were present in the dataset due to logging glitches.
* **Impact:** Distorted order counts and artificially inflated revenue figures.
* **Fix Applied:** Deduplicated using `df.drop_duplicates(subset=['Order_ID'], keep='first')`.

 3. Data Type Formatting
* **Issue:** `Order_Date` was stored as a string (`object`) instead of a proper date format.
* **Impact:** Inability to run time-series filtering or group by month/year.
* **Fix Applied:** Standardized to `datetime64[ns]` using `pd.to_datetime(df['Order_Date'])`.

## ⚙️ How to Setup and Run
1. Clone the Repository
```bash
git clone [https://github.com/kamanikumari12/apexplanet-sales-analysis.git](https://github.com/kamanikumari12/apexplanet-sales-analysis.git)
cd apexplanet-sales-analysis
