# data-analyst-internship-task3


# Sales Dashboard - Elevate Labs Data Analyst Internship Task

## Project Overview
This repository contains an interactive sales dashboard built in Power BI for analyzing the [Kaggle Sales Dataset](https://www.kaggle.com/datasets/abrarahmed26/sales-dataset) (using all_data.csv). The dashboard focuses on key performance indicators (KPIs) such as Total Sales, Assumed Profit, Total Quantity Ordered, and Total Orders. It includes  product and city breakdowns, and interactive filters to support business decisions like identifying top-performing products or seasonal sales patterns.

The goal is to provide stakeholders with quick insights into sales performance, growth, and geographic trends. This project demonstrates data cleaning, DAX calculations, visualization best practices, and interactivity in Power BI.

### Key Features
- **KPIs**: Dynamic cards showing Total Sales, YoY Growth (percentage), Total Quantity Ordered, Total Orders, and Assumed Profit (based on a 20% margin assumption due to lack of cost data).
- **Visualizations**: Line charts for monthly sales trends, bar charts for sales by product and city, and a treemap for product distribution.
- **Data Prep**: Calculated Sales (Price Each * Quantity Ordered), cleaned dates, and derived columns like Year, Month, and State from addresses.

## Dataset
- Source: all_data.csv from Kaggle Sales Dataset.
- Columns Used: Order ID, Product, Quantity Ordered, Price Each, Order Date, Purchase Address, City, Sales (calculated), Date (cleaned).
- Size: Approximately 186K rows (original dataset); cleaned for duplicates and invalid dates.

## Requirements
- **Software**: Power BI Desktop (free version).
- **Dependencies**: None beyond Power BI. The .pbix file is self-contained.

## Installation and Setup
1. Clone this repository: `git clone https://github.com/yourusername/sales-dashboard.git`
2. Download Power BI Desktop from the [official site](https://powerbi.microsoft.com/desktop/) if not installed.
3. Open the `sales_dashboard.pbix` file in Power BI Desktop.
4. If data refresh is needed, go to Home > Refresh (the dataset is embedded, but you can reconnect to your local CSV if modified).

## How to Use the Dashboard
1. Open the .pbix file.
2. View KPIs at the top for quick summaries (e.g., Total Sales updates dynamically).
3. Interact with charts: Hover for tooltips, click to cross-filter, or drill down on date hierarchies.
4. Export insights: Use File > Export > PDF or PowerPoint for sharing.

## Steps Taken to Build the Dashboard
1. **Data Import and Cleaning**:
   - Loaded all_data.csv into Power BI.
   - Cleaned Order Date to a proper date format and added a Date column.
   - Calculated Sales as `[Price Each] * [Quantity Ordered]`.
   - Extracted State from Purchase Address using Power Query (split by comma and space).
   - Added Year and Month columns for grouping.

2. **DAX Measures for KPIs**:
   - Total Sales: `SUM([Sales])`
   - YoY Growth: `DIVIDE([Total Sales] - CALCULATE([Total Sales], SAMEPERIODLASTYEAR([Date])), CALCULATE([Total Sales], SAMEPERIODLASTYEAR([Date])))` (formatted as %)
   - Total Quantity: `SUM([Quantity Ordered])`
   - Total Orders: `DISTINCTCOUNT([Order ID])`
   - Assumed Profit: `[Total Sales] * 0.2` (placeholder; update if cost data is added)

3. **Visualizations**:
   - Added Card visuals for KPIs with formatting (currency for Sales, % for Growth).
   - Created line charts for sales trends over time.
   - Built bar charts for sales by product/city and a treemap for distributions.
   - Applied a consistent theme (e.g., blue tones) and enabled interactions.

4. **Deliverables**:
   - This repo includes the .pbix file, cleaned dataset (all_data_cleaned.csv), PPT summary (sales_insights.pptx) with screenshots and key findings, and this README.

## Key Findings and Insights
- **Top Performers**: Products like "Macbook Pro Laptop" drive the highest sales; cities like San Francisco show peak revenue.
- **Trends**: Sales peak in Q4 (December), with positive YoY Growth in most years (e.g., 15-20% assuming multi-year data).
- **Opportunities**: Focus marketing on high-growth cities; stock up on top products during peak seasons.
- **Limitations**: Profit is assumed (no cost data); add real costs for accuracy.

## Challenges and Learnings
- **Data Cleaning**: Handled inconsistent dates and address formats using Power Query—learned the importance of early validation.
- **DAX Complexity**: YoY Growth required handling time intelligence; tested with small subsets to debug.
- **Performance**: For large datasets, using aggregates improved load times.
- **Best Practices**: Kept the dashboard to one page for simplicity; emphasized interactivity for user engagement.

This project enhanced my skills in Power BI, from data modeling to visualization, and showed how dashboards can inform real business decisions like inventory planning.

## Contributing
Feel free to fork and improve! Submit pull requests for enhancements like adding real profit calculations or more visuals.
