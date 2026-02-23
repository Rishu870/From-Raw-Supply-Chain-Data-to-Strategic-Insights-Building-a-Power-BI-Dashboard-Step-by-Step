# From-Raw-Supply-Chain-Data-to-Strategic-Insights-Building-a-Power-BI-Dashboard-Step-by-Step
Step 1: Cleaning and Preparing the Data in Power Query
Before analysis begins, data preparation is critical.

1. Renaming Columns for Clarity
Some column names were too long for clean visuals, especially KPI cards. So I simplified them:

Number of Products Sold → Product Sold
Revenue Generated → Revenue
Manufacturing → Mfg
Manufacturing Lead Time → Mfg Lead Time
Manufacturing Costs → Mfg Costs
Clear naming improves readability and dashboard presentation.

2. Always Check Data Types
One of the most important habits in Power BI:

✔ Ensure numeric fields are numbers
✔ Ensure percentages are decimals
✔ Ensure categorical fields remain text

Incorrect data types cause incorrect calculations.

You can also go to:

View Tab → Column Quality & Column Distribution

This allows you to:

Check valid values
Detect nulls
Identify distribution patterns
Spot inconsistencies early
This step prevents errors later in DAX.

Step 2: Creating Custom Columns for Smarter Analysis
To build a meaningful supply chain dashboard, I created analytical columns.

Custom Column 1: Total Costs
To understand profitability, I first needed the total cost:

Which we can see in the image below

Press enter or click to view image in full size

Total Costs = [Mfg costs] + [Shipping costs] + [Costs]
This aggregates:

Manufacturing cost
Shipping cost and
Transportation cost
Custom Column 2: Profit Margin
Next, I calculated the actual profit:

Press enter or click to view image in full size

Profit Margin = [Revenue] - [Total Costs]
Custom Column 3: Profit Margin %
To standardize performance comparisons, I created a custom column to calculate the profit margin percentage.

Press enter or click to view image in full size

% Profit Margin = [Profit Margin] / [Revenue] * 100
Important:
After creating these columns, Power Query assigned them as Text data types.

I manually converted them to:

Decimal Number
Whole Number (where appropriate)
This is to ensure that our DAX measures work correctly.

Step 3: Creating a Dedicated Measures Table
To keep the model clean and professional, I created a separate table for measures.

This improves:

Organization
Readability
Scalability
Step 4: Creating Core Measures for Analysis
These were the measures used in the dashboard:

Total Revenue
Total Revenue = SUM(supply_chain_data[Revenue])
Total Product Sold
Total Product Sold = SUM(supply_chain_data[Product Sold])
Total Cost
Total Cost = SUM(supply_chain_data[Mfg costs]) +
SUM(supply_chain_data[Shipping costs]) +
SUM(supply_chain_data[Costs])
Stock Level
Stock Level = SUM(supply_chain_data[Stock levels])
Order Quantity
Order Quantity = SUM(supply_chain_data[Order quantities])
Average Profit Margin %
Avg Profit Margin % = AVERAGE(supply_chain_data[% Profit Margin])
Average Defect Rate
Avg Defect Rate % = AVERAGE(supply_chain_data[Defect rates])* 100
Average Price
Average Price = AVERAGE(supply_chain_data[Price])
These measures power all KPI cards and visuals.

Final Dashboard Structure
The report includes three main pages: the Overview Page, the Supplier Insight Page, and the Product Insight Page.

Press enter or click to view image in full size

Overview Page
1. Overview
Total Revenue
Total Product Sold
Total Cost
Average Profit Margin %
Stock Level
Revenue by Product Type
Revenue by Shipping Carrier
Revenue by SKU
Defect Rate by Product Type
Press enter or click to view image in full size

Product Insight Page
2 Product Insight
Order Quantities by SKU
Stock Levels by SKU
Lead Time vs Mfg Lead Time
Profit Margin % by Product Type
Price vs Quantity Sold Scatter Plot
Press enter or click to view image in full size

Supplier Insight Page
3 Supplier Insight
Total Cost by Transportation Mode
Average Defect Rate by Transportation Mode
Supplier Performance Comparison
Supplier Profit vs Defect Scatter Plot
Supplier Stock Levels
Key Insights from the Analysis
Certain shipping carriers generate higher revenue contributions.
Defect rates vary significantly across transportation modes.
Some suppliers show high profit margin but also high defect rate — a quality risk.
Manufacturing lead time impacts product availability.
A few SKUs contribute disproportionately to revenue.
This demonstrates how supply chain analytics can improve:
✔ Operational efficiency
✔ Supplier selection
✔ Logistics cost control
✔ Product profitability

Power BI becomes powerful when structure meets strategy.

