# Advanced Power BI DAX Dashboard 🧮

## 📌 Project Overview
Built an advanced Power BI dashboard using DAX measures on an African 
Business Sales dataset covering 5,000 transactions across 5 countries 
from 2021–2024.

## 🛠️ Tools Used
- Power BI Desktop
- DAX (Data Analysis Expressions)
- Power Query (M Language)

## 📂 Dataset
- African Business Sales Dataset (custom built)
- 5,000 rows, 23 columns
- Countries: South Africa, Nigeria, Kenya, Ghana, Egypt

## 🧮 DAX Measures Created

### Basic Measures
```dax
Total Sales = SUM(BI_Sales_Dataset[Sales])

Total Profit = SUM(BI_Sales_Dataset[Profit])

Total Orders = COUNTROWS(BI_Sales_Dataset)

Profit Margin % = DIVIDE(SUM(BI_Sales_Dataset[Profit]), 
                  SUM(BI_Sales_Dataset[Sales])) * 100

Average Order Value = DIVIDE(SUM(BI_Sales_Dataset[Sales]), 
                     COUNTROWS(BI_Sales_Dataset))

Return Rate % = DIVIDE(SUM(BI_Sales_Dataset[Returns]), 
               COUNTROWS(BI_Sales_Dataset)) * 100
```

### Time Intelligence Measures
```dax
YTD Sales = 
CALCULATE(
    SUM(BI_Sales_Dataset[Sales]),
    DATESYTD('Date Table'[Date])
)

Sales Last Year = 
CALCULATE(
    SUM(BI_Sales_Dataset[Sales]),
    DATEADD('Date Table'[Date], -1, YEAR)
)

YoY Growth % = 
DIVIDE([YTD Sales] - [Sales Last Year], 
       [Sales Last Year]) * 100
```

### Advanced Measures
```dax
Running Total Sales = 
CALCULATE(
    SUM(BI_Sales_Dataset[Sales]),
    FILTER(
        ALLSELECTED('Date Table'),
        'Date Table'[Year] <= MAX('Date Table'[Year])
    )
)

Sales Performance = 
SWITCH(
    TRUE(),
    SUM(BI_Sales_Dataset[Sales]) >= 20000000, "High Performer",
    SUM(BI_Sales_Dataset[Sales]) >= 10000000, "Mid Performer",
    "Low Performer"
)
```

## 📊 Dashboard Pages

### Page 1 — Sales Dashboard
- KPI Cards: Total Sales, Total Profit, Total Orders
- Time Intelligence Cards: YTD Sales, Sales Last Year, YoY Growth %
- Sales by Category Bar Chart
- Total Profit by Region Column Chart
- Sales Over Time Line Chart
- Profit Margin by Category Bar Chart

### Page 2 — Customer Dashboard
- Top 5 Customers using RANKX
- Sales Performance Table using SWITCH
- Running Total Sales Line Chart

## 💡 Key DAX Concepts Demonstrated
- SUM, COUNTROWS, DIVIDE — basic aggregations
- CALCULATE — context modification
- TOTALYTD, SAMEPERIODLASTYEAR, DATEADD — time intelligence
- FILTER, ALL, ALLSELECTED — filter manipulation
- RANKX — dynamic customer ranking
- SWITCH — conditional segmentation
- VAR / RETURN — variables in DAX
- Date Table using CALENDAR function

## 💡 Key Business Insights
- Technology drives the most revenue across all categories
- Consistent sales growth from 2021 to 2024
- North region leads in total profit
- Top 5 customers drive significant revenue

## 🖼️ Dashboard Screenshot
<img width="767" height="431" alt="image" src="https://github.com/user-attachments/assets/c7eeb6c8-bd62-4bfa-a1e4-cf5db3a31625" />
<img width="788" height="507" alt="image" src="https://github.com/user-attachments/assets/30ad0eaa-b917-49af-9282-1d453a119400" />


## 🔗 Full Project Write-Up
[View on Notion Portfolio](https://merciful-coconut-e1f.notion.site/Ompha-Ramaru-Data-Analyst-Portfolio-3498a09bc57780a8851ed774fa74d0b6)
