
# 📊Exploratory Data Analysis for Walmart Sales Data

This document summarizes SQL queries executed on the **FactSales** dataset and provides observations and analysis for each.

---

## 🧾1. Inspecting the First Few Records
**Query:**
```sql
SELECT TOP 5 * FROM FactSales;
```
**🔍Purpose:**  
To get a quick look at the data structure and sample records.

<img width="951" height="162" alt="image" src="https://github.com/user-attachments/assets/b07ecd5f-21c5-4d53-ad23-1cbe46390adc" />

**🧠Observation:**  
We see fields such as `DateKey`, `StoreKey`, `Quantity`, `UnitPrice`, `SalesAmount`, `ProfitAmount`, `Discount`, and `TransactionDate`.  

**📈Analysis:**  
This helps in understanding the schema and verifying that data types align with expectations.

---

## 🔢 2. Counting Total Records in FactSales
**Query:**
```sql
SELECT COUNT(*) FROM FactSales;
```
<img width="187" height="78" alt="image" src="https://github.com/user-attachments/assets/317b862a-8031-4877-993b-5c1be8dc0cf3" />

**🧠Observation:**  
FactSales contains **10,051** records.

**📈Analysis:**  
A moderate dataset size, suitable for analytical queries without major performance concerns.

---

## 🏬 3. Counting Stores in DimStore
**Query:**
```sql
SELECT COUNT(*) FROM DimStore;
```
<img width="192" height="80" alt="image" src="https://github.com/user-attachments/assets/fc04bba6-3ed4-4d0f-98d7-67b5c868cc07" />

**🧠Observation:**  
There are **100** unique stores.

**📈Analysis:**  
Each store has contributed multiple transactions to the FactSales table.

---

## ❌ 4. Checking for Missing SalesAmount
**Query:**
```sql
SELECT COUNT(*) FROM FactSales WHERE SalesAmount IS NULL;
```
<img width="186" height="76" alt="image" src="https://github.com/user-attachments/assets/2a4112ce-09da-4ae3-8eb9-04ceb8ccbf5e" />

**🧠Observation:**  
There are **0 null values** in SalesAmount.

**📈Analysis:**  
No missing revenue data; calculations on sales can be considered reliable.

---

## 🔁 5. Identifying Stores with Multiple Transactions
**Query:**
```sql
SELECT StoreKey, COUNT(*) 
FROM FactSales 
GROUP BY StoreKey 
HAVING COUNT(*) > 1;
```
<img width="237" height="396" alt="image" src="https://github.com/user-attachments/assets/770f42fe-7a49-454b-b471-65ea9ea02766" />

**🧠Observation:**  
Every store has multiple transactions; counts range widely across stores.

**📈Analysis:**  
Sales are well-distributed, though some stores (e.g., StoreKey `10037`, `9988`) show significantly higher activity.

---

## 📐 6. Sales Distribution Statistics
**Query:**
```sql
SELECT AVG(SalesAmount), MIN(SalesAmount), MAX(SalesAmount), STDEV(SalesAmount) 
FROM FactSales;
```
<img width="403" height="75" alt="image" src="https://github.com/user-attachments/assets/2da3cb41-f01c-487d-84b6-b6df2bc0fec4" />

**🧠Observation:**  
- Average Sale: ~120.87  
- Min Sale: 0.00  
- Max Sale: 993.00  
- Std Dev: ~112.49  

**📈Analysis:**  
Sales amounts vary greatly. The minimum being `0.00` may suggest free or test transactions.

---

## 📅 7. Monthly Sales Trend
**Query:**
```sql
SELECT d.Year, d.Month, SUM(f.SalesAmount) 
FROM FactSales f JOIN DimDate d 
ON f.DateKey = d.DateKey 
GROUP BY d.Year, d.Month 
ORDER BY d.Year, d.Month;
```
<img width="240" height="395" alt="image" src="https://github.com/user-attachments/assets/bfb6d8ac-a776-451e-879f-e21bab06053a" />

**🧠Observation:**  
Sales show clear seasonality and growth over years, peaking in **2019** and **2023**, then declining in 2024–2025.

**📈Analysis:**  
This could reflect external market conditions or changes in business strategy. Seasonal peaks (Nov–Dec) suggest holiday shopping influence.

---

## 💳 8. Sales by Payment Method
**Query:**
```sql
SELECT p.PaymentMethod, COUNT(*), SUM(f.SalesAmount) 
FROM FactSales f 
JOIN DimPaymentMethod p 
ON f.PaymentMethodKey = p.PaymentMethodKey 
GROUP BY p.PaymentMethod 
ORDER BY total_sales DESC;
```
<img width="302" height="118" alt="image" src="https://github.com/user-attachments/assets/44007029-6296-4eb0-a806-3aa758acc256" />

**🧠Observation:**  
- Credit Card: 489k  
- Ewallet: 457k  
- Cash: 268k  

**📈Analysis:**  
Cash usage is lower, while digital payments dominate. Indicates a tech-savvy customer base.

---

## 📆 9. Sales by Weekend vs Weekday
**Query:**
```sql
SELECT d.IsWeekend, COUNT(*), SUM(f.SalesAmount) 
FROM FactSales f 
JOIN DimDate d 
ON f.DateKey = d.DateKey 
GROUP BY d.IsWeekend;
```
<img width="272" height="98" alt="image" src="https://github.com/user-attachments/assets/d71a9287-1049-4c21-9adb-0399e74d437f" />

**🧠Observation:**  
- Weekdays: 7132 transactions (~851k sales)  
- Weekends: 2919 transactions (~363k sales)

**📈Analysis:**  
Weekday sales are more than double weekend sales, possibly indicating more shopping during working days.

---

## 🧴 10. Sales by Product Category
**Query:**
```sql
SELECT c.CategoryName, AVG(f.UnitPrice), AVG(f.ProfitAmount), SUM(f.Quantity), SUM(f.SalesAmount) 
FROM FactSales f 
JOIN DimCategory c 
ON f.CategoryKey = c.CategoryKey 
GROUP BY c.CategoryName 
ORDER BY total_sales DESC;
```
<img width="507" height="178" alt="image" src="https://github.com/user-attachments/assets/5de53da1-865a-406c-b152-14f8bbb69845" />

**🧠Observation:**  
- **Top Categories:** Home & Lifestyle, Fashion Accessories (nearly equal sales ~492k each).  
- **Least Sales:** Health & Beauty (~47k).  

**📈Analysis:**  
Focus should be on top-selling categories while exploring why Health & Beauty underperforms.

---

## 🗺️ 11. Sales by City
**Query:**
```sql
SELECT s.City, SUM(f.SalesAmount) 
FROM FactSales f 
JOIN DimStore s 
ON f.StoreKey = s.StoreKey 
GROUP BY s.City 
ORDER BY city_sales DESC;
```
<img width="203" height="391" alt="image" src="https://github.com/user-attachments/assets/43bd2189-ae1a-4094-8555-d7e393345ce4" />

**🧠Observation:**  
- Highest sales: **Weslaco (46k)**, Waxahachie (41k).  
- Lowest sales: **Lake Jackson (5k)**.

**📈Analysis:**  
There is a strong geographical imbalance; certain cities are driving most of the revenue.

---

## 📦 12. Sales by CategoryKey
**Query:**
```sql
SELECT CategoryKey, SUM(SalesAmount), SUM(Quantity) 
FROM FactSales 
GROUP BY CategoryKey;
```
<img width="297" height="177" alt="image" src="https://github.com/user-attachments/assets/28faa28c-afdd-4c67-b7ab-e4ae141aed38" />

**🧠Observation:**  
- CategoryKey 6 & 1 dominate (~492k each).  
- CategoryKey 2 (Health & Beauty) lags behind.

**📈Analysis:**  
Corroborates earlier category analysis — resources should be allocated to expanding top-performing categories.

---

# 📌 Final Insights
1. **📈Strong growth** in sales till 2019 and 2023, with recent declines in 2024–25.  
2. **💳Credit cards and e-wallets dominate** payments, showing customer preference for digital modes.  
3. **📅Weekdays outperform weekends**, an unusual retail trend that merits further investigation.  
4. **🧴Category concentration:** A few categories dominate revenue, indicating dependency risk.  
5. **🗺️Geographic skew:** Certain cities like Weslaco and Waxahachie lead disproportionately.

---

# Recommendation
- 🔍Investigate decline in 2024–25 sales.  
- 🎯Encourage weekend shopping through promotions.  
- 🧪Explore strategies to uplift weaker categories (Health & Beauty, Sports).  
- 💡Consider loyalty programs tied to digital payments.

