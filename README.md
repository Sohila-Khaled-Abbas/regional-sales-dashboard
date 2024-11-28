
# Regional Sales Dashboard 📊

### **Overview**

The **Regional Sales Dashboard** is a dynamic and interactive data visualization project developed using **Power BI**. This dashboard provides actionable insights into **Sales**, **Profit**, and **Number of Orders** across different regions and timeframes. It helps businesses identify trends, measure performance, and make data-driven decisions.

---

### **Features**

- **Sales Analysis**:
  - Displays total sales for selected years.
  - Monthly trends visualized through bar charts with a trendline.
  - Highlights year-over-year (YoY) growth or decline using intuitive color coding.

- **Profit Analysis**:
  - Shows total profit with comparisons to previous years.
  - Provides monthly breakdowns with green/red highlights for profit gains or losses.
  - Includes drilldown functionality to analyze profit by **Region**, **State**, or **City**.

- **Order Volume**:
  - Summarizes the total number of orders per year.
  - Tracks monthly order volume trends and identifies peak months.

- **Regional Breakdown**:
  - Compares Sales, Profit, and Order Volume across regions.
  - Highlights top-performing regions with the ability to drill down into finer details.

---

### **Technologies Used**

- **Power BI** for dashboard design and data visualization.
- **Microsoft Excel** for data preparation and initial analysis.
- **GitHub** to store and manage project assets, including datasets and screenshots.

---

### **Project Files**

| File/Folder Name        | Description                                                                 |
|-------------------------|-----------------------------------------------------------------------------|
| `Regional Sales Dashboard.pbix` | Power BI file containing the complete dashboard.                            |
| `datasets/`             | Folder containing the raw and cleaned CSV datasets used in the project.    |
| `screenshots/`          | Folder with screenshots of the dashboard visualizations.                   |
| `visualizations.md`     | Detailed descriptions of key dashboard visualizations with screenshots.    |
| `data-preprocessing-steps.md` | Document explaining the data cleaning and transformation process.           |

---

### **Project Goals**

1. **Understand Regional Sales Trends**: Gain insights into how sales, profit, and orders vary by region, state, and city.
2. **Track Yearly Performance**: Monitor yearly changes in key metrics and identify growth opportunities.
3. **Make Data-Driven Decisions**: Use visualization to support decision-making and identify actionable areas for improvement.

---

### **How to Use the Dashboard**

1. **Download the `.pbix` File**:
   - Clone this repository and download the `Regional Sales Dashboard.pbix` file from the root folder.
2. **Open in Power BI**:
   - Ensure Power BI Desktop is installed on your machine.
   - Open the `.pbix` file in Power BI to explore the dashboard interactively.
3. **Interact with Filters**:
   - Use the **Year** and **Region** slicers to filter the data dynamically.
   - Drill down into bar charts for state- and city-level insights.

---

### **Screenshots**

Below are examples of visualizations included in the dashboard. For more details, check the `visualizations.md` file.

#### **1. Sales Overview**
![Sales Overview](screenshots/sales-overview.png)

#### **2. Profit Trends**
![Profit Trends](screenshots/profit-trends.png)

#### **3. Number of Orders**
![Order Volume](screenshots/order-volume.png)

#### **4. Regional Breakdown**
![Regional Breakdown](screenshots/regional-performance.png)

---

### **How to Contribute**

We welcome contributions! Here’s how you can get involved:
1. **Fork the repository** and create a feature branch.
2. **Report issues** or request features using GitHub Issues.
3. **Submit a pull request** for new features or bug fixes.

---

### **How to Upload Data and Screenshots to GitHub**

#### **Uploading Datasets**:
1. Save your cleaned and raw datasets as `.csv` files.
2. Place them in a `datasets/` folder in the repository.
3. Use the following commands to upload:
   ```bash
   mkdir datasets
   mv /path/to/dataset.csv datasets/
   git add datasets/
   git commit -m "Added datasets"
   git push origin main
   ```

#### **Uploading Screenshots**:
1. Capture screenshots of your dashboard visualizations.
2. Save them in a `screenshots/` folder.
3. Upload using Git:
   ```bash
   mkdir screenshots
   mv /path/to/screenshot.png screenshots/
   git add screenshots/
   git commit -m "Added screenshots for visualizations"
   git push origin main
   ```

---

### **Future Enhancements**

- **Integration with Real-Time Data**: Enhance the dashboard by connecting it to live data sources.
- **Additional Metrics**: Add customer demographics or sales forecasts to deepen insights.
- **Custom Themes**: Improve visual aesthetics by exploring advanced Power BI themes.

---

### **License**
This project is licensed under the MIT License. See the `LICENSE` file for more details.

---

### **Acknowledgments**
Special thanks to the creators of the **Power BI** tool and the open-source community for their resources and support.


