# Coffee-Dashboard-Report
The Coffee Data Project analyzes sales, customer behavior, and product performance to deliver actionable insights through a dynamic dashboard.

---
# ☕ Horizon Coffee Sales Dashboard

Beyond daily reporting, the **Horizon Coffee Dashboard** acts as a strategic compass for decision-making. By continuously tracking key performance indicators (KPIs), the team can uncover growth opportunities, detect inefficiencies early, and react quickly to market shifts.

## 🎯 Project Objective
The Horizon Coffee Sales Dashboard helps the business see how well different roast types and package sizes sell, how much profit is earned, and which regions or customers drive revenue. It converts thousands of transactions into easy-to-read visuals that highlight trends, compare results, and reveal what works or does not. With just a few clicks, users can explore which roast sells best, which country brings in the most money, or which months are busiest for sales.

Managers, baristas, and decision makers get fast answers without digging through spreadsheets. The dashboard supports smarter choices about inventory, marketing focus, and pricing. Whether planning next quarter or reviewing last year’s results, it shines a light on the numbers that matter most.

## 📁 Datasets Used
| File | Description |
|------|-------------|
| [`data/orders.csv`](data/orders.csv) | Order-level records with dates, quantities, sales, and profit |
| [`data/products.csv`](data/products.csv) | Product catalog with roast type and size |
| [`data/customers.csv`](data/customers.csv) | Customer IDs and loyalty status |
| [`Dashboard & Pivot Tables.xlsx`](Dashboard%20&%20Pivot%20Tables.xlsx) | Excel workbook containing pivot tables and the final dashboard |

_All sensitive information has been removed or anonymized._

## ❓ Key Questions
- 💵 What are total sales, profit, and quantity sold overall?  
- ☕ Which roast types and package sizes generate the highest sales?  
- 👤 Which customers are the most valuable?  
- 📅 What monthly trends appear in sales and profit?  
- 🌍 Which countries drive the most revenue?  
- 📊 How does a loyalty card influence sales?  
- 📈 Which seasonal patterns repeat over time?  
- 🧮 How do product choices affect profit margins?  

## 🧭 Process Workflow
1. **Data Collection**  
   Exported raw order, product, and customer tables from the café POS into CSV.

2. **Data Cleaning & Structuring**  
   Removed duplicates, fixed date formats, standardized country names, and filled in missing values.

3. **Data Aggregation**  
   The **Coffee Data Project – Cleaned Datasets Orders** sheet was enriched with customer and product attributes, plus calculated metrics, using the following formulas (unchanged here for reference):

   | Purpose | Formula |
   |---------|---------|
   | **Return Customer Name** | `=XLOOKUP(C2,customers!$A$2:$A$1001,customers!$B$2:$B$1001,0)` |
   | **Return Customer Email** | `=IF(XLOOKUP(C2,customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0)=0,"",XLOOKUP(C2,customers!$A$1:$A$1001,customers!$C$1:$C$1001,0))` |
   | **Return Customer Phone** | `=XLOOKUP(C2,customers!$A$2:$A$1001,customers!$G$2:$G$1001,0)` |
   | **Return Loyalty Card (Yes/No)** | `=XLOOKUP(orders!$C2,customers!$A$1:$A$1001,customers!$I$1:$I$1001,,0)` |
   | **Return Coffee Type Code** | `=INDEX(products!$A$1:$H$49,MATCH(orders!$D2,products!$A$1:$A$49,0),MATCH(orders!I$1,products!$A$1:$H$1,0))` |
   | **Return Roast Type Code** | `=INDEX(products!$A$1:$H$49,MATCH(orders!$D2,products!$A$1:$A$49,0),MATCH(orders!J$1,products!$A$1:$H$1,0))` |
   | **Sales (Value)** | *Quantity × Unit Price* |
   | **Profit (Value)** | *Unit Price × Price per 100 g* |
   | **Decode Coffee Type Name** | `=IF(I2="Rob","Robusta",IF(I2="Exc","Excelsa",IF(I2="Ara","Arabica",IF(I2="Lib","Liberica"))))` |
   | **Decode Roast Type Name** | `=IF(J2="M","Medium",IF(J2="L","Large",IF(J2="D","Dark","")))` |

4. **Dashboard Design**  
   The finished Excel dashboard combines several visual elements to keep insights clear and intuitive:

   | Visual Type | Purpose in the Dashboard |
   |-------------|--------------------------|
   | **Timeline slicer** | Interactive date filter lets users slide through years, quarters, or months and instantly update every chart. |
   | **Scorecards (KPI cards)** | Display single high-level numbers—Total Sales, Total Profit, Quantity Sold, and Profit Margin—so performance is clear at a glance. |
   | **Vertical bar chart** | Shows *Sales & Profit by Month* to reveal seasonal spikes and dips. |
   | **Horizontal bar chart** | Compares *Sales by Country* side-by-side, highlighting the United States outlier. |
   | **Line chart** | Plots *Total Sales Over Time* (separate colored lines for each coffee type) to expose long-term growth trends and product volatility. |

   A consistent coffee-brown palette and clear labels keep the visuals on brand and easy to interpret.

5. **User Interactivity**  
   - Slicers for date, roast type, size, and loyalty card allow quick drill-down.  
   - An interactive version of the dashboard is hosted on Google Drive: **[Coffee Data project – Dashboard & Pivot Tables](https://docs.google.com/spreadsheets/d/1s6qi2ya9JtE3qqRXDyeL5gQdFMK9hRFF/edit?usp=sharing&ouid=104140290870922976550&rtpof=true&sd=true)**.  
     **Important:** download and open this file in **Excel 2013 or later**—Google Sheets cannot render the timeline slicer, KPI scorecards, or pivot-table-driven charts correctly.

## 📊 Dashboard Snapshot
![Horizon Coffee Dashboard](images/Sales%20Coffee%20Dashboard%20Screenshot.png)

## 📈 Key Insights
- **Total Sales**: $45,134  
- **Total Profit**: $8,156  
- **Total Quantity Sold**: 3,551 units  
- **Top Country**: United States – $35,639 in sales  
- **Other Markets**: Ireland $6,697, United Kingdom $2,799  
- **Top Customers**: Allis Wilmore $317, Brenn Dundredge $307, Terri Farra $289, Nealson Cutler $282, Don Flintliff $278  
- **Roast Trends**: Excelsa spiked in mid-2021, Robusta surged during holiday months  
- **Loyalty Impact**: Loyalty card holders placed frequent repeat orders, lifting average spend  

# 📊 Project Insights
- KPI cards provide an instant view of sales and profit performance, boosting overall business visibility.  
- Interactive slicers let users drill into roast type, country, or loyalty status, leading to sharper decisions.  
- Monthly trend analysis reveals clear seasonal peaks that guide staffing, inventory, and promotion timing.  
- Country and customer segmentation highlights strong regions and high-value buyers, informing marketing spend.  
- Roast-level analysis exposes both popular and underperforming beans, steering purchasing and menu design.  
- Simple visuals make complex data approachable for non-technical teams, encouraging a data-driven culture.  
- Centralized metrics improve transparency across operations, finance, and marketing.  
- The project lays the groundwork for future enhancements like demand forecasting, customer lifetime value analysis, and automated alerts.  

## 🧠 Strategic Use of KPIs for Future Planning
With these insights, Horizon Coffee can:

- Forecast next year’s sales using historical trends.  
- Focus marketing on the United States and replicate its winning tactics in Ireland.  
- Schedule promotions when Excelsa and Robusta demand peaks.  
- Refine loyalty perks to retain top customers and lift revenue per order.  
- Align bean purchasing and staffing with predictable seasonal demand.  

## 🧾 Conclusion
The Horizon Coffee Sales Dashboard turns raw sales logs into a single, easy-to-read source of truth that updates in real-time, letting every team spot revenue swings, seasonal surges, and high-value customers at a glance. By pairing timeline slicers, scorecards, and focused charts, it guides smarter stocking, targeted marketing, and leaner operations—while laying a clean data foundation for future forecasting and customer-insight models. In short, it’s a compact control center that helps Horizon Coffee move from guesswork to data-driven growth with just a couple of clicks.

---
