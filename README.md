
---

# 📊 Tailwind Traders Sales Dashboard

An advanced Power BI report analyzing **global sales data** for **Tailwind Traders**, a fictitious retail company. The project demonstrates expertise in **data modeling, DAX, performance optimization, and storytelling with Power BI**.

---

## 🚀 Project Sequence

### 1️⃣ Project Objective

Tailwind Traders aims to strengthen strategic decision-making by gaining detailed insights into **sales, profitability, and customer engagement** across multiple regions.
The dashboard empowers stakeholders to:

* Monitor **Gross Revenue, Net Revenue, Profit, and Tax**
* Track **Yearly, Quarterly, and YTD Profit Margins**
* Perform **currency conversion into USD** for consistent reporting
* Drill down by **country, product, and customer attributes**

---

### 2️⃣ Data Sources

* **Excel Files** (Coursera-provided dataset)

  * Sales Table (Gross Product Price, Gross Revenue, Net Revenue, Total Tax, Quantity)
  * Purchases & Customers Table
  * Country-level loyalty data
* **Python Script**

  * Generated **Exchange Rates Table** using a pandas script for multiple currencies
* **Power BI (Power Query)**

  * Calendar Table for **time intelligence (YTD, QTD)**
  * Sales in USD using DAX

---

### 3️⃣ Tools & Skills Used

* **Microsoft Power BI Desktop**
* **Data Modeling** & Relationship Building
* **DAX Measures**

  * `TOTALYTD()`, `DATESQTD()`, `DIVIDE()`, `MEDIAN()`
* **Performance Analyzer** for optimization (<400ms load time)
* **Row-Level Security (RLS)** for secure access
* **Python for ETL** (exchange rate table)
* **Power Query** for cleaning & transformations

---

### 4️⃣ Data Preparation Workflow

1. **Data Cleaning & Formatting**

   * Removed duplicates & handled missing values in Power Query
2. **Data Modeling**

   * Star Schema:

     * **Fact Table:** Sales
     * **Dimension Tables:** Customers, Products, Calendar, Exchange Rates
3. **Currency Conversion**

   * Implemented **USD Conversion** via Python-based Exchange Rate Table & DAX
4. **Calendar Table**

   * Generated with DAX to enable time intelligence functions
5. **DAX Calculations**

   * **Yearly Profit Margin** = `(Net Revenue – Total Tax) / Gross Revenue`
   * **Quarterly Profit** = `DATESQTD([Profit])`
   * **YTD Profit** = `TOTALYTD([Profit], 'Calendar'[Date])`
   * **Median Sales** = `MEDIAN(Sales[Net Revenue])`

---

### 5️⃣ Dashboard Structure (Single PBIX File)

#### 📍 **Sales Overview Page**

* **Bar Chart:** Loyalty Points by Country
* **Column Chart:** Quantity Sold by Product
* **Pie Chart:** Median Sales by Country
* **Line Chart:** Median Sales Over Time
* **KPI Cards:** Stock, Quantity Purchased, Median Sales
* **Slicer:** Country filter

#### 📍 **Profit Overview Page**

* **Bar Chart:** Net Revenue by Product
* **Donut Chart:** Yearly Profit Margin by Country
* **Area Chart:** Yearly Profit Margin Over Time
* **Cards:** YTD Profit, Net Revenue USD
* **KPI Visual:** Gross Revenue Trend
* **Slicer:** Date Range

#### 📍 **DAX Aggregation & Performance Page**

* Benchmarked visuals in **Performance Analyzer**
* Removed non-essential visuals post-testing
* Achieved **report load times under 400ms**

---

### 6️⃣ Key Insights

#### **Sales Report**

* **UK** leads in loyalty points, signaling strong customer retention.
* **Top Products:** Floral Wallpaper, Porcelain Dinner Set, ProCarpenter Toolkit.
* **France** dominates in **median sales**, while **Australia & UAE lag**.
* Median Sales show **high volatility over time** → unstable growth trend.

#### **Profit Report**

* **Electric Water Heater** generates the **highest net revenue**.
* **USA** shows **highest yearly profit margin**, **UAE lowest**.
* Profit Margins peaked in **August**, declined in **September**, then recovered in October.

---

### 7️⃣ Recommendations

* **Enhance Loyalty Programs**

  * Boost UAE engagement with regionalized promotions.
* **Inventory Optimization**

  * Stock & promote top-selling products for consistent availability.
* **Stabilize Sales Trend**

  * Investigate seasonal demand fluctuations & launch targeted campaigns.
* **Profit Margin Improvement**

  * Focus on **low-performing regions (UAE)** with pricing & cost optimization.
* **Address Seasonal Declines**

  * Develop promotional strategies to counteract September downturns.

---

### 8️⃣ Project Outcome

This project demonstrates advanced Power BI skills:
- ✅ **Interactive, layered dashboards** with drill-through functionality
- ✅ **Efficient DAX measures** for time intelligence and profit analysis
- ✅ **Performance-optimized visuals** (<400ms load time)
- ✅ **Row-Level Security implementation** for secure stakeholder reporting
- ✅ **Business Insights** → Data-driven strategies for profitability and loyalty management

---

### 📂 Repository Structure (for GitHub Portfolio)

```
Tailwind-Traders-Sales-Dashboard/
│── README.md
│── Tailwind_Traders_Sales.pbix
│── visuals/
│    ├── Sales_Overview.png
│    ├── Profit_Overview.png
│    └── DAX_Performance.png
│── scripts/
│    └── exchange_rates.py
│── docs/
     └── Tailwind_Traders_Sales_Report.pdf
```

---

