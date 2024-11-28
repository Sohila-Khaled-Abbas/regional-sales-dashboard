# Data Preprocessing Steps for Regional Sales Dashboard

This document outlines the data preparation steps performed in Power BI to clean and process the raw sales data.

---

## **1. Data Sources**
- **Source File**: `raw-sales-data.csv`
- **Data Fields**:
  - Order Date
  - Sales Revenue
  - Profit
  - Region
  - State
  - City

---

## **2. Data Cleaning Process**
1. **Remove Duplicates**:
   - Identified and removed duplicate rows based on the following columns:
     - `Order ID`
     - `Order Date`
     - `Region`

2. **Handle Missing Values**:
   - Checked for missing or null values in key columns (`Sales Revenue`, `Profit`, and `Order Date`).
   - Applied the following fixes:
     - Replaced missing `Profit` values with **0**.
     - Dropped rows with missing `Order Date` values.

3. **Correct Inconsistent Data**:
   - Standardized region names (e.g., "Central", "East", "West", "South").
   - Fixed date formats in the `Order Date` column (converted to `YYYY-MM-DD`).

4. **Create New Columns**:
   - Extracted `Month` and `Year` from `Order Date` for trend analysis:
     ```dax
     Month = FORMAT([Order Date], "MM")
     Year = FORMAT([Order Date], "YYYY")
     ```
   - Added a `Profit Margin` column:
     ```dax
     Profit Margin = DIVIDE([Profit], [Sales Revenue], 0)
     ```

5. **Filter Outliers**:
   - Excluded transactions with negative `Sales Revenue`.

---

## **3. Data Transformation**
1. **Aggregations**:
   - Created summaries at the region and state level to analyze sales trends.
   - Aggregated the following metrics:
     - Total `Sales Revenue`
     - Total `Profit`
     - Count of Orders

2. **Data Modeling**:
   - Applied a star schema with:
     - A fact table containing `Order ID`, `Sales Revenue`, and `Profit`.
     - Dimension tables for `Region`, `State`, and `Date`.

---

## **4. Output Files**
- **Cleaned Dataset**: `cleaned-sales-data.csv`
  - Contains columns: `Order ID`, `Order Date`, `Sales Revenue`, `Profit`, `Region`, `State`, `City`, `Month`, `Year`, `Profit Margin`.

- **Raw Dataset**: `raw-sales-data.csv` (for comparison).

---

## **Visualization Features Based on Cleaned Data**
- Dynamic filtering by `Year` and `Region`.
- Key performance indicators (KPIs):
  - Sales vs. Previous Year
  - Profit Growth
  - Order Counts
- Regional breakdown for performance comparison.

---

