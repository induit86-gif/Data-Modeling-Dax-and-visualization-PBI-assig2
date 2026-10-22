# Data-Modeling-Dax-and-visualization-PBI-assig2# Power BI Assignment 2 – DAX & Data Visualization

## 📊 Project Overview

This project is part of my **Data Analytics – Module 2: Power BI** learning journey. As an aspiring Data Analyst, I am developing my skills in DAX (Data Analysis Expressions), business intelligence, data visualization, and dashboard development using Power BI.

The objective of this project is to analyze an E-Commerce Sales Dataset, calculate meaningful business metrics, compare actual sales with sales targets, and build interactive visualizations to identify sales trends, profitability, and business performance.

## 🎯 Project Objectives

- Create calculated columns using DAX.
- Develop measures to calculate sales, profit, and order counts.
- Perform Year-to-Date (YTD) sales analysis.
- Compare actual sales against sales targets.
- Analyze sales and profit performance by category, sub-category, state, and city.
- Design an interactive Power BI dashboard to communicate business insights.

## 📁 Dataset Description

The project uses three datasets from the E-Commerce Sales Dataset.

### 1. List of Orders
Contains order-level information.

**Columns:** Order ID, Order Date, Customer Name, City, State, Category, Amount, Profit.

### 2. Order Details
Contains product and sub-category-level information.

**Columns:** Order ID, Category, Sub-Category, Quantity, Amount, Profit.

### 3. Sales Target
Contains monthly sales targets by category.

**Columns:** Category, Month of Order Date, Target.

These datasets support the analysis of sales performance, profitability, product categories, geographical distribution, and target achievement.

## 🧹 Data Model

The data model and relationships were created as part of **Power BI Assignment 1 – Data Transformation & Data Modeling**.

The existing model is used as the foundation for DAX calculations and visualizations in this assignment.

Key considerations:
- Verify relationships between the order, order details, and sales target tables.
- Ensure matching data types for relationship columns.
- Validate the granularity of each table to prevent duplicated sales or target values.
- Use an appropriate Date table for accurate time-intelligence calculations.

## 🧮 DAX Calculations

### 1. Calculated Columns

**Category Type**

Combines Category and Sub-Category into a single column in the Order Details table.

```dax
Category Type =
'Order Details'[Category] & " - " &
'Order Details'[Sub-Category]
```

**Revenue per Order**

Calculates revenue using Amount multiplied by Quantity, as specified in the assignment.

```dax
Revenue per Order =
'Order Details'[Amount] *
'Order Details'[Quantity]
```

**Sales Category**

Classifies records as Above Average or Below Average based on Amount.

```dax
Sales Category =
IF(
    'Order Details'[Amount] >
    AVERAGE('Order Details'[Amount]),
    "Above Average",
    "Below Average"
)
```

### 2. Calculated Measures

**Order Count**

Counts distinct orders in the Order Details table.

```dax
Order Count =
DISTINCTCOUNT('Order Details'[Order ID])
```

**Average Profit in Delhi**

Calculates the average profit for orders placed in Delhi.

```dax
Average Profit in Delhi =
CALCULATE(
    AVERAGE('List of Orders'[Profit]),
    'List of Orders'[City] = "Delhi"
)
```

**Total Sales**

```dax
Total Sales =
SUM('List of Orders'[Amount])
```

**Total Profit**

```dax
Total Profit =
SUM('List of Orders'[Profit])
```

**Total Sales Target**

```dax
Total Sales Target =
SUM('Sales Target'[Target])
```

**Year-to-Date (YTD) Sales**

Calculates cumulative sales from the beginning of the year through the selected date, using a properly configured Date table.

```dax
YTD Sales =
TOTALYTD(
    [Total Sales],
    'Date'[Date]
)
```

*Note: The Date table must be created or configured and related correctly to the order date. Adjust table and column names if they differ in the Power BI model.*

## 📈 Data Visualizations

The report includes the following visualizations to explore business performance.

| Visualization | Chart Type | Purpose |
|---|---|---|
| Sales Target Achievement by Category | Clustered Column Chart | Compares actual sales with targets across categories. |
| Max Profit Margin by Sub-Category | Donut Chart | Displays profit-margin performance across sub-categories. |
| Monthly Sales Trend | Line Chart | Identifies monthly sales patterns and changes over time. |
| Profit vs Quantity by Sub-Category | Scatter Chart | Examines the relationship between profit and quantity sold. |
| Total Sales Amount vs Target | Card Visuals | Highlights actual sales and sales targets. |
| Minimum Target by Segment | Multi-row Card | Displays the minimum target for each relevant segment. |
| Sales Performance Matrix | Matrix | Compares actual sales and targets by category and month. |
| Geographic Sales Analysis | Map | Displays sales distribution across cities. |
| Sales Distribution by Sub-Category | Treemap | Shows the relative contribution of each sub-category to sales. |
| Order Count by State | Funnel Chart | Compares order counts across states. |

**Note:** For profit-margin analysis, define the margin calculation consistently, such as Profit divided by Sales Amount, and use the maximum margin at the intended level of detail. Confirm that the fields and aggregations used in each visual match the assignment requirements.

## 📊 Dashboard Design

The Power BI report brings together the DAX calculations and visualizations into a structured reporting experience.

Dashboard design principles:
- Clear titles and descriptive labels.
- Consistent formatting and number formats.
- Appropriate chart types for each analytical question.
- Readable axes, legends, and data labels.
- Meaningful layout and spacing.
- Interactive filtering using slicers where appropriate.

## 🔍 Business Questions Addressed

This project aims to answer the following business questions:

1. How do actual sales compare with sales targets across product categories?
2. Which sub-categories contribute most to sales?
3. How do sales change month by month?
4. Which sub-categories generate higher profits?
5. What is the relationship between quantity sold and profit?
6. How are sales distributed across cities and states?
7. How many distinct orders are recorded?
8. What is the average profit for orders placed in Delhi?
9. How does cumulative YTD sales performance change over time?

## 🛠️ Tools & Technologies

- **Microsoft Power BI Desktop** – Report development and dashboard design.
- **DAX** – Calculated columns, measures, aggregations, and time intelligence.
- **Power Query Editor** – Data preparation and transformation from the previous assignment.
- **Data Modeling** – Relationships between related tables.
- **GitHub** – Project documentation and portfolio management.

## 📂 Project Structure

```text
Power-BI-Assignment-2-DAX-Visualization/
│
├── README.md
├── Power BI Assignment 2.pbix
├── screenshots/
│   ├── dax-calculations.png
│   ├── sales-target-analysis.png
│   ├── monthly-sales-trend.png
│   └── dashboard-overview.png
│
└── documentation/
    └── Power-BI-Assignment-2-Report.pdf
```

*Replace the example filenames with the actual filenames in your repository. Include only files and screenshots you have created.*

## 📦 Deliverables

- Power BI `.pbix` file containing the data model, DAX calculations, measures, and visualizations.
- PDF report containing screenshots of DAX formulas, visualizations, and the dashboard layout.
- README documentation explaining the project objectives, methodology, and analytical approach.

## 🎓 Skills Demonstrated

Through this project, I am developing practical skills in:

- DAX calculated columns and measures.
- Data aggregation and filter context.
- Time-intelligence calculations.
- Sales and profitability analysis.
- Sales target comparison.
- Data visualization and dashboard design.
- Business interpretation and analytical thinking.
- Technical documentation and portfolio development.

## 💡 Key Learnings

This assignment helps me understand how DAX transforms raw data into meaningful business metrics, how relationships affect calculations, and how different visualizations communicate business performance.

It also strengthens my ability to present data clearly and support business decisions through interactive reporting.

## 🚀 Conclusion

This project represents an important step in my journey toward becoming a Data Analyst. By combining data modeling, DAX calculations, and interactive visualizations, I am building a foundation in business intelligence and practical data analysis.

I will continue expanding my portfolio with projects that demonstrate my analytical skills, technical knowledge, and ability to turn data into actionable insights.

---

**Author:** Aspiring Data Analyst  
**Project:** Power BI Assignment 2 – DAX & Data Visualization  
**Module:** Data Analytics – Module 2  
**Tools:** Power BI Desktop, DAX, Power Query, GitHub
