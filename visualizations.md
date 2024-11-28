# Regional Sales Dashboard Visualizations

## Overview

The **Regional Sales Dashboard** offers a comprehensive analysis of sales, profit, and order data across multiple regions and years (2020-2023). The dashboard utilizes interactive elements like slicers, bar charts, line charts, and more to give stakeholders insights into key metrics. The following sections break down each of the visualizations and the DAX formulas used to create them.

---

## 1. Sales Overview by Year

### Description:
- The **Sales Overview** visualization displays total sales over time (monthly) for each year (2020, 2021, 2022, and 2023). The user can select a specific year from the slicer, which will update the data dynamically across all visualizations.
- This visualization is a line chart that tracks sales performance month by month, with comparison features for year-over-year growth.

### Key Features:
- **Line Chart**: Shows monthly sales over multiple years.
- **Year-over-Year Comparison**: Dynamic feature comparing selected year to the previous year.

### Metric:
- **Total Sales** in USD.

### DAX Formula:
```dax
Total Sales = SUM(Sales[SalesAmount])
```
## 2. Profit Overview by Year
### Description:
- This bar chart shows total profit for each month across the years. The profit is calculated as the difference between revenue and cost.
- The user can view profit trends month by month and compare the profit figures across different years.
### Key Features:
- **Bar Chart**: Displays monthly profit figures for each year.
- **Profit Trend**: Shows positive or negative profit growth over time.
### Metric:
- **Total Profit** in USD.
### DAX Formula:
```dax
Total Profit = SUM(Profit[ProfitAmount])
```
## 3. Orders Overview by Region
### Description:
- This stacked bar chart visualizes the total number of orders placed each month, broken down by region (Central, East, South, and West).
- The regions are shown on the Y-axis, and the X-axis displays the total number of orders per month.
### Key Features:
- **Stacked Bar Chart**: Displays order volume by region for each month.
- **Dynamic Filtering**: Users can filter by year or region to analyze specific areas or time periods.
### Metric:
- **Total Orders** (number of orders).
### DAX Formula:
```dax
Total Orders = COUNT(Orders[OrderID])
```
## 4. Regional Breakdown by Sales, Profit, and Orders
### Description:
- This visualization provides a detailed breakdown of sales, profit, and order data by region (Central, East, South, and West). Users can click on a region to filter the data and gain deeper insights into that specific region’s performance.
- It also features drillthrough functionality for more detailed exploration at the state or city level.
### Key Features:
- **Bar Chart**: Visualizes sales, profit, and orders by region.
- **Drillthrough**: Allows users to click on a region for a deeper dive into the data by state or city.
### Metrics:
- **Sales, Profit, and Orders** by region.
## 5. Year-over-Year Comparison of Sales
### Description:
- This line chart shows sales growth or decline by comparing the selected year against the previous year. It is helpful for identifying seasonal patterns or year-over-year improvements.
### Key Features:
- **Line Chart**: Shows year-over-year sales data.
- **Color Coding**: Positive growth is shown in green, and negative growth in red.
### DAX Formula for Year-over-Year Comparison:
```dax
YoY Sales = 
VAR PreviousYearSales = CALCULATE(SUM(Sales[SalesAmount]), SAMEPERIODLASTYEAR(DateTable[Date]))
RETURN
IF(ISBLANK(PreviousYearSales), BLANK(), SUM(Sales[SalesAmount]) - PreviousYearSales)
```
---
## Data Preprocessing Steps
### Data Cleaning and Transformation:
The following steps were applied to clean and transform the data before creating the visualizations:
1. **Remove Duplicates**:
- Duplicate rows were removed based on key columns such as *Order ID*, *Sales Amount*, and *Region*.
2. **Handle Missing Values**:
- Rows with missing values in critical fields like *Sales Amount*, *Profit*, and *Order Date* were removed, and null values were replaced or filtered out.
3. **Standardizing Data**:
- Region names were standardized to consistent formats (e.g., "Central", "East", "West").
- The *Order Date* column was formatted into the correct date format (*YYYY-MM-DD*).
4. **Creating Calculated Columns**:
- Month and Year columns were derived from the Order Date for time-based analysis:
``` dax
Month = FORMAT([Order Date], "MM")
Year = FORMAT([Order Date], "YYYY")
```
5. **Outlier Removal**:
- Outliers such as negative sales values were removed to maintain data integrity.
6. **Aggregating Data**:
- Aggregated metrics (total sales, profit, orders) were calculated at different levels, such as by region, state, and city.
---
## Conclusion:
- The **Regional Sales Dashboard** provides a dynamic and comprehensive analysis of sales, profit, and order trends over time. By utilizing interactive elements such as slicers and drill-down features, users can explore the data from multiple angles and make informed business decisions.

- These visualizations, combined with the DAX calculations and data cleaning steps, make it easier to uncover valuable insights and identify opportunities for business growth.

