# AtliQ Hardware - Business 360 - Dashboard

### Dashboard Link : https://shorturl.at/uIY8d

## Problem Statement

**AtliQ Hardware**, a global electronics manufacturing powerhouse, recently encountered a significant setback in Latin America. Despite their rapid expansion, the company's ill-fated venture was marked by substantial losses. Their reliance on traditional methods, such as surveys, spreadsheets, and intuition, proved to be a costly gamble.

To rectify this situation and ensure future success, AtliQ is strategically adopting data analytics. My role in this transformative project is to develop comprehensive reports that offer a multifaceted view of the business. By delving into various departments, including finance, sales, marketing, and supply chain, I'll provide actionable insights that empower stakeholders to make informed decisions.

These reports will not only highlight key performance indicators but also uncover hidden trends and patterns. By analyzing vast datasets, I'll identify opportunities for optimization, risk mitigation, and strategic growth. Ultimately, my goal is to equip AtliQ with the data-driven intelligence necessary to navigate the complexities of the global electronics market and achieve long-term prosperity.



### Steps followed 

- Step 1 : Connected Power BI to MySQL database and imported data.

- Step 2 : Created relationships between tables (Data Modeling).

- Step 3 : Created a date table in Power BI using M language and Power Query editor.

- Step 4 : Data validation in Power BI against the benchmark numbers provided by the product owner.

- Step 5 : Reviewed rough sketches of the finance view dashboard sent by a product owner. Used power query M formula language and some other features (such as merge tables) to generate a single table containing both actuals and estimates.

- Step 6 : Added fiscal_year to fact_sales_estimate, performed left outer join between two tables, created a new column for Gross Sales and Net Invoice Sales.

- Step 7 : Built a few dimension tables to establish one-many relationships in the data model.

- Step 8 : Created additional calculated columns such as net sales and COGS to complete rest of the P&L metrics.

- Step 9 : Optimized report size by performing instrumentation through a tool called DAX studio.
 
- Step 10 : Created various DAX measures that were used to build visuals for the finance view.

- Step 11 : Created a static table with P&L rows that could serve as a template for P&L visual. Created a DAX measure to connect P&L rows table with different measures that we created earlier with the use of SWITCH formula.

          P&L Values = var res = SWITCH (
        TRUE(),
        MAX('P & L Rows'[Order]) = 1, [GS $]/10^6,
        MAX('P & L Rows'[Order]) = 2, [Pre Invoice Deductions]/10^6,
        MAX('P & L Rows'[Order]) = 3, [NIS $]/10^6,
        MAX('P & L Rows'[Order]) = 4, [Post Invoice Deductions]/10^6,
        MAX('P & L Rows'[Order]) = 5, [Post Invoice Other Deductions]/10^6,
        MAX('P & L Rows'[Order]) = 6, ([Post Invoice Deductions] + [Post Invoice Other Deductions])/10^6,
        MAX('P & L Rows'[Order]) = 7, [NS $]/10^6,
        MAX('P & L Rows'[Order]) = 8, [Manufacturing Cost]/10^6,
        MAX('P & L Rows'[Order]) = 9, [Freight Cost]/10^6,
        MAX('P & L Rows'[Order]) = 10, [Other Costs]/10^6,
        MAX('P & L Rows'[Order]) = 11, [COGS]/10^6,
        MAX('P & L Rows'[Order]) = 12, [GM $]/10^6,
        MAX('P & L Rows'[Order]) = 13, [GM %]*100,
        MAX('P & L Rows'[Order]) = 14, [GM/Unit],
        MAX('P & L Rows'[Order]) = 15, [total_operational_cost]/10^6,
        MAX('P & L Rows'[Order]) = 16, [NP $]/10^6,
        MAX('P & L Rows'[Order]) = 17, [NP %]*100
         )
        return 
        IF(HASONEVALUE('P & L Rows'[Description]), res, ([NS $]/10^6))
  

- Step 12 : Created LY (Last Year) column for P&L visual. Added fiscal year description as a calculated column for better readability by appending “ Est” (Estimated Values) to a future year.

- Step 13 : Created a single DAX measure called P & L Final value that can show selected year’s values in P&L visual using DAX functions like: ALLNOBLANKROW, UNION, SELECTEDVALUE, MAX.
         P&L Final Value = SWITCH(TRUE(),SELECTEDVALUE(fiscal_year[FY_Description]) = MIN('P&L Columns'[Column Header]), [P&L Values],
    MIN('P&L Columns'[Column Header])= "P&L Values", [P&L Values],
    MIN('P&L Columns'[Column Header])= "BM", [P&L BM],
    MIN('P&L Columns'[Column Header])= "Change", [Change],
    MIN('P&L Columns'[Column Header])= "Change %", [Change %])
    

- Step 14 : Built Finace view which includedes: a line chart, top products, categories, and, segments and top regions, and markets using a matrix visual.
        
        
- Step 15 : Built Sales view that includes: Top customers table with Net Sales (NS), Gross Margin (GM), and Gross Margin % (GM%).Scatter chart having Net Sales and Gross Margin on its axis and showing market and region as the bubbles on the chart. A table representing top products (along with category and segments). A donut chart showing a percentage contribution of Net Sales, Post Invoice Deductions, Pre-Invoice Deductions. Another donut chart showing a percentage breakdown of Total COGS and Gross Margin.


        
 - Step 16 :Built marketing view that includes: Top products table (along with segments and categories), Unit economics (donut chart and a stacked column chart), Gross Margin vs Net Sales matrix, Top markets table (markets along with a region)
 
 
 - Step 17 : Created the following measures for the supply chain view, Net Error and Net Error %, ABS Error and ABS Error %, Forecast Accuracy

 - Step 18 : Built the Supply chain view which includes: Supply chain metrics table (Forecast accuracy %, Net error, Risk, etc.) for customers and for products. A column and line chart containing the monthly trend of supply chain metrics.

- Step 19 : Built the Executive view which includes: Market share trends, yearly trends of key metrics, insights by sub zone, top 5 products and customers by revenue, net sales by channel and divison.

 
 - Step 20 : The report was then published to Power BI Service after making appropriate changes as per the suggestions made in the meetings with the stakeholders.
 
 
# Home Page
![Screenshot 2024-10-15 161948](https://github.com/user-attachments/assets/e7fbec60-b373-4935-b36a-531b81256db7)

# Finance View
![Screenshot 2024-10-15 151408](https://github.com/user-attachments/assets/e2287c21-0c41-4321-bb48-874fbe5f02e1)

### [1] Insights from Finance View

- **Revenue Growth:** The company experienced substantial revenue growth from 2018 to 2022, but fell short of its 2022 targets by 1.86%.
- **Regional Performance:** While most regions demonstrated strong growth, Latin America, particularly Colombo, underperformed.
- **Product Challenges:** Networking sales declined over the past three years, despite a stable gross margin.
- **Market Focus:** European markets like France, the Netherlands, and Austria represent opportunities for growth in networking products.

*Despite significant overall revenue growth, the company missed its 2022 targets  by 1.86% and faces challenges in specific regions and product segments.*


# Sales View
![Screenshot 2024-10-15 151428](https://github.com/user-attachments/assets/5ed76fb3-f6e4-4272-98c8-113fb63c0527)

### [2] Insights from Sales View

- **Customer Performance:** 'Nova' has consistently generated the lowest net sales from 2020 to 2022, despite maintaining a gross margin of 25-30%.
- **Discounting Strategy:** The company's sales department appears to be offering significant discounts to 'Nova,' but this has not translated into higher sales.
- **Product Focus:** Networking products have consistently been the lowest-selling category.
- **Discount Analysis:** The scatter chart reveals that multiple customers are underperforming in terms of gross margin. The donut charts indicate that the company relies heavily on discounts to achieve its sales targets, resulting in lower margins.

*Despite consistent discounts, 'Nova' remains a low-performing customer with the lowest gross margin. The company's overall sales strategy appears to rely heavily on discounting, leading to lower margins.*


# Marketing View
![Screenshot 2024-10-15 151448](https://github.com/user-attachments/assets/eb38e778-458f-4110-b4ee-a9e3dc1437ae)

### [3] Insights from Marketing View

- **Product Performance:** Notebooks have high sales but low margins, while peripherals and accessories have low sales and margins.
- **Profitability Analysis:** Net profit percentage follows a similar pattern, indicating a need to increase margins and reduce operational costs.
- **Product Positioning:** Products with low net profit should be repositioned to maximize sales and profitability.
- **Cost Management:** The company's operational costs exceed gross margins, resulting in losses.
- **Performance Analysis:** The matrix visuals highlight specific products and markets that require attention to improve net profit.

*The company faces challenges in balancing profitability and sales volume across product segments. Strategic adjustments are needed to improve margins, reduce costs, and optimize product positioning.*




# Supply Chain View
![Screenshot 2024-10-15 151504](https://github.com/user-attachments/assets/62bbfcc7-fa7f-4227-908b-94f188b2d037)

### [4] Insights from Supply Chain View

- **Forecast Accuracy:** The forecast accuracy has increased by 1.2% compared to the previous year, reaching 81.17% in the current year.
- **Stockouts and Errors:** Despite the improved accuracy, the company still experienced 3472.7K item stockouts and 6899K items were wrongly forecasted in 2022.
- **Inventory Deficiencies:** The net error, as represented by the bar chart, shows that inventory deficiencies are increasing, even with improved forecast accuracy.

*Despite improved forecast accuracy, the company continues to face challenges with stockouts and forecasting errors, particularly for certain customers and products.*

# Executive View
![Screenshot 2024-10-15 151524](https://github.com/user-attachments/assets/90b78675-140a-4e4c-9848-82fa9a37f0c5)

### [5] Insights from Executive View

- **Market Share Growth:** Atliq's market share increased significantly from 2021 to 2022, growing from 1.06% to 5.87%.
- **Performance Improvements:** Forecast accuracy, net sales, and gross margin percentage have all improved compared to previous years.

*Atliq has rapidly gained market share since 2021, but profitability remains a challenge, despite improvements in forecast accuracy, net sales, and gross margin.*















           

