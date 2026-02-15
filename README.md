# 📊 Sales Performance Analysis – Executive Dashboard (Power BI)

---

## 📌 Project Overview

This project delivers an executive-level Power BI dashboard designed to provide a clear and interactive view of sales performance.

The dashboard enables:

- Year-over-Year (YoY) performance comparison  
- Monthly trend analysis  
- Geographic distribution visualization  
- Segment and regional performance breakdown  
- Category-level profit contribution analysis  

The objective is to provide decision-makers with a concise yet drillable performance overview.

---

## 🎯 Business Challenge

How can leadership quickly evaluate overall performance while maintaining visibility into regional, segment, and product-level drivers?

The solution combines high-level KPIs with interactive drill-down capabilities to support structured performance analysis.

---

## 🛠 Technical Stack

- Power BI
- DAX (Advanced Time Intelligence)
- Data Modeling (Fact Table + Dedicated Date Dimension)
- Business Logic Encapsulation
- KPI Custom Visual Design

---

### 🖥️ Desktop Version
> [!TIP]
> This version includes interactive tooltips for granular data exploration.

![Sales Dashboard Overview](assets/sales-dashboard-desktop.png)

---

### 📱 Mobile Optimization
> [!IMPORTANT]
> Fully responsive layout designed for executive-level monitoring on smartphones.

![Sales Dashboard Mobile Overview](assets/sales-dashboard-mobile.png)

---

## 🔍 Key Insights (2015 Executive Snapshot)

Based on the selected year:

- Sales declined by 2.8% YoY, while profit increased by 24.4%, suggesting margin improvement.
- The Consumer segment accounts for 46% of total profit, making it the primary profit driver.
- A clear seasonality pattern is observed, with peak performance in November (Q4 concentration).
- Phones emerge as the leading profit-generating category.

Overall, the dashboard highlights improved profitability despite declining revenue.

---

## 🧭 Strategic Interpretation & Recommendations

Based on the 2015 performance snapshot:

### 1️⃣ Profitability Resilience Despite Revenue Decline

Despite declining revenue, profitability improved significantly.

This suggests:
- Improved margin structure  
- Potential pricing adjustments  
- Product mix optimization  

**Recommendation:**  
Investigate high-margin product categories and replicate successful pricing or cost-control strategies across lower-performing segments.


### 2️⃣ Segment Concentration Risk

The Consumer segment represents the largest share of total profit.

**Opportunity:**  
Further scale this segment through targeted marketing and loyalty strategies.

**Risk:**  
Over-dependence on a single segment may increase exposure if demand shifts.


### 3️⃣ Strong Seasonality Effect

Performance peaks in Q4, especially in November.

**Recommendation:**  
- Optimize inventory planning before Q4  
- Reinforce promotional campaigns ahead of peak demand  
- Analyze margin variation during high-volume months  


### 4️⃣ Category-Level Profit Drivers

Phones dominate profit contribution.

**Recommendation:**  
- Evaluate cross-selling opportunities  
- Assess dependency on specific product categories  
- Monitor competitive pricing pressure in top-performing categories  


### 5️⃣ Regional Performance Imbalance

Regional performance varies significantly, with East and West outperforming South.

**Recommendation:**  
Investigate:
- Regional demand patterns  
- Operational efficiency differences  
- Local competitive dynamics  

Targeted regional strategy may unlock additional growth potential.

---

## 🚀 Technical Highlights

### 🔹 Data Model Design
The model is structured around a centralized sales table supported by a dedicated Date dimension to ensure reliable time intelligence calculations.

### 🔹 Advanced DAX & Time Intelligence
Robust Year-over-Year measures with strict filter context control and edge case handling (e.g., missing historical data).

### 🔹 Centralized Business Logic
Reusable measures ensure metric consistency across all levels of granularity (Year, Month, Region, Segment).

### 🔹 Custom KPI Cards
Hybrid KPI visuals combining:
- Absolute values
- YoY variation
- Directional indicators (▲ ▼)

All within a clean executive UI.

### 🔹 Multidimensional Analysis
Interactive performance exploration by:
- Region
- Customer Segment
- Product Category
- Geographic distribution

Systematic comparison with Prior Year (PY).

### 🔹 Executive-Oriented UX
Clear information hierarchy and high signal-to-noise ratio for rapid insight consumption.

---

## 🧠 Technical Deep Dive: DAX Logic 
To demonstrate my technical proficiency, here are two key implementations from the project:

### 1. Robust Data Modeling (Date Table)
Instead of relying on Power BI's "Auto Date/Time", I developed a custom Calendar table to ensure consistent time intelligence and optimized model performance.

```dax
Dim_Date = 
ADDCOLUMNS (
    CALENDAR ( MIN ( Fact_Sales[Order Date] ), MAX ( Fact_Sales[Order Date] ) ),
    "Year", YEAR ( [Date] ),
    "Month", FORMAT ( [Date], "MMM" ),
    "Month Number", MONTH ( [Date] )
)
```

### 2. DAX Ingenuity (Dynamic KPI Card)
One of the key technical challenges was to create a streamlined executive view. Instead of using multiple visuals, I developed a custom DAX measure to consolidate the **Value**, **Trend Indicator**, and **YoY Percentage** into a single, high-impact label.

### Total Profit + YoY Measure:
```dax
Total Profit + YoY = 
VAR ProfitValue = [Total Profit]
VAR ProfitValueK = ProfitValue / 1000
VAR YoY = [Profit YoY %]
VAR Arrow =
    IF(
        YoY > 0,
        "▲ ",
        IF(YoY < 0, "▼ ", "")
    )

RETURN
IF(
    ISBLANK(ProfitValue),
    BLANK(),
    FORMAT(ProfitValueK, "#,##0") & "K $ " &
    Arrow &
    FORMAT(YoY, "+0.0%;-0.0%")
)
```   

## 📈 Business Impact

✔ Immediate visibility into revenue-profit divergence and performance gaps   
✔ Clear visibility of profit drivers (Phones, Paper, etc.)  
✔ Strategic cross-analysis across geography and segments  
✔ Faster data-driven decision-making  

---

## 💾 Data Source

The analysis is based on the Sample Superstore dataset, a standard retail dataset used to demonstrate advanced Business Intelligence capabilities.

---

## 📁 Project Architecture

The repository is structured to clearly separate assets, documentation, and analytical development files.

- **assets/** → Dashboard screenshots  
- **docs/** → Business documentation and analytical notes  
- **pbix/** → Power BI development file

---

## 👤 Author

**Emmanuel Chevalier**  
Data Analyst | Power BI & DAX  
Microsoft Power BI Data Analyst (Coursera)
