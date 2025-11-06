# 📊 Financial KPI Dashboard — Power BI + DAX  

## 🚀 Overview  
This project is an **interactive Financial Analytics Dashboard** built in **Power BI**, designed to track and visualize key performance indicators (KPIs) such as **Revenue**, **Profit**, **Liquidity**, and **YoY Growth**.  
The goal is to demonstrate advanced **DAX (Data Analysis Expressions)** skills and business-oriented data storytelling through insightful visualizations.  

---

## 🧩 Dataset  
**Columns used:**  
- `Date`  
- `Department`  
- `Region`  
- `Revenue`  
- `Expense`  
- `Net_Profit`  
- `Assets`  
- `Liabilities`  
- `Liquidity_Ratio`  

---

## 🧮 DAX Measures Used  

### 🏦 Financial KPIs  
```DAX
Total Revenue = SUM('Financial'[Revenue])
Total Expense = SUM('Financial'[Expense])
Total Profit = SUM('Financial'[Net_Profit])
Profit Margin % = DIVIDE([Total Profit], [Total Revenue], 0)
Liquidity Ratio = AVERAGE('Financial'[Liquidity_Ratio])
```

### 📅 Time Intelligence

```DAX
YTD Profit = TOTALYTD([Total Profit], 'Financial'[Date])

YoY Profit Growth % =
VAR CurrentYear = YEAR(TODAY())
VAR CurrentYearProfit =
    CALCULATE([Total Profit], YEAR('Financial'[Date]) = CurrentYear)
VAR LastYearProfit =
    CALCULATE([Total Profit], YEAR('Financial'[Date]) = CurrentYear - 1)
RETURN
DIVIDE(CurrentYearProfit - LastYearProfit, LastYearProfit, 0)
```

### 🥇 Ranking Metrics

```DAX
Profit Rank by Region =
RANKX(ALL('Financial'[Region]), [Total Profit], , DESC)
```

### 🎨 Conditional KPI Formatting

```DAX
YOY_Color =
SWITCH(
    TRUE(),
    [YoY Profit Growth %] > 0.15, "Green",
    [YoY Profit Growth %] >= 0.05, "Yellow",
    "Red"
)
```

### 📈 Dashboard Highlights

- Dynamic KPIs: Displays total revenue, expenses, profit, and YoY growth.

- Profit Trend Visualization: YoY and YTD charts to track financial health.

- Ranking Chart: Region-wise profit ranking with conditional color formatting.

- Interactive Filters: Region, Department, and Year slicers for flexible analysis.

- Storytelling Design: Clean layout optimized for business decision-making.

### 🧠 Learnings & Focus

- Strengthened understanding of DAX context transitions and time intelligence.

- Practiced data storytelling through visuals and KPIs.

- Improved dashboard aesthetics using conditional formatting and hierarchies.

### 🛠️ Tools & Technologies

- Power BI Desktop

- DAX (Data Analysis Expressions)

- Microsoft Excel / CSV for data preprocessing

### 🌟 Future Enhancements

- Integrate forecasting using DAX + AI Insights.

- Add drill-through pages for department-level analysis.

- Automate dataset refresh with Power BI Service.
