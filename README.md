# Superstore Sales Analysis Power BI Report (2014-2017)
This Power BI report presents an analysis of Superstore sales data from 2014 to 2017. The objective is to analyze various sales trends, cart value segments, delivery times, and performance by category and year to provide actionable insights.

# Key Features
# KPIs:

Total Sales: $2.33M
Sales from Products with Discount: $0.92M
Sales from Low Cart Category: $1.28M
Sales from Low Cart and Discount > 50%: $14.11K

# Slicers:

Year
Category

# Visualizations:

MTD and YTD Hierarchical View: Displays detailed sales breakdown for Month-to-Date (MTD) and Year-to-Date (YTD).
Sales by Cart Value: A visual representation of sales segmented by cart value. The "Low Cart Value" segment contributes the highest with 54.7% of total sales.
Average Days in Delivery by Ship Mode: Shows the average delivery time for each ship mode. "Standard Class" has the highest delivery time of 5 days.
Sales YTD by Quarter: A breakdown of YTD sales by quarter, with Q4 showing the highest sales of $2.33M.
DAX Functions Used
The following DAX functions were used to calculate key metrics such as MTD, YTD, and others:

1. YTD (Year-To-Date) Calculation
To calculate YTD sales, the following DAX function is used:

# DAX

YTD Sales = 
TOTALYTD(
    SUM(Sales[Sales Amount]),
    Sales[Order Date]
)
Explanation: The TOTALYTD function sums the sales for the year up to the current date for each record in the data. It uses the Order Date as the date field.

2. MTD (Month-To-Date) Calculation
To calculate MTD sales, the following DAX function is used:

DAX
Copy
Edit
MTD Sales = 
TOTALMTD(
    SUM(Sales[Sales Amount]),
    Sales[Order Date]
)
Explanation: The TOTALMTD function sums the sales for the current month up to the current date for each record in the data, using the Order Date as the date field.

3. Sales from Products with Discount
To calculate sales from products that have a discount, the following DAX function is used:

DAX

Sales with Discount = 
CALCULATE(
    SUM(Sales[Sales Amount]),
    Sales[Discount] > 0
)
Explanation: The CALCULATE function is used to sum sales where the Discount field is greater than 0.

4. Sales from Low Cart Category
To calculate sales from the "Low Cart" category, you can use a similar approach:


Sales from Low Cart = 
CALCULATE(
    SUM(Sales[Sales Amount]),
    Sales[Cart Value] < 100
)
Explanation: The CALCULATE function is used to filter and sum sales where the Cart Value is less than a defined threshold, like 100 in this case.

5. Sales from Low Cart and Discount > 50%
For sales from low cart value and a discount greater than 50%, the following DAX function is used:

Sales Low Cart & Discount > 50 = 
CALCULATE(
    SUM(Sales[Sales Amount]),
    Sales[Cart Value] < 100,
    Sales[Discount] > 0.5
)
Explanation: This calculation filters sales where the Cart Value is below 100 and the Discount is greater than 50% before summing the sales.

# Data
The report uses sales data from the Superstore dataset spanning the years 2014 to 2017. The dataset includes fields like Product, Category, Cart Value, Discount, Ship Mode, Sales, and more.

# Getting Started
Clone this repository or download the Power BI (.pbix) file.
Open the file in Power BI Desktop.
Interact with the report using the slicers and various visuals to explore the sales data.
Prerequisites
Power BI Desktop (latest version recommended)
Sample Superstore Sales Dataset (included in the report)

# Usage
This report is designed for business analysts, data analysts, or anyone looking to gain insights into Superstore sales data, focusing on:
Performance of sales across categories.
Trends in sales by cart value.
Analysis of sales by discounts and low cart values.
Delivery times for different shipping modes.
