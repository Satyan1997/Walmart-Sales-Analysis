# 🛍️ Walmart Sales & Performance Dashboard  
**Retail Intelligence Reimagined | Powered by Star Schema**

## 📖 Project Overview

This project explores Walmart’s retail performance across 100 stores in 98 cities using a custom-built dashboard powered by a Star Schema data warehouse. The goal is to uncover actionable insights across time, geography, product categories, payment behavior, and customer engagement.

We chose Walmart for its scale and complexity—making it the perfect canvas for retail analytics. This dashboard transforms raw data into strategic intelligence.

---

## 🧠 Data Architecture: Star Schema

The dashboard is built on a Star Schema for efficient querying and intuitive filtering.

**Fact Table: `SalesFact`**
- SalesAmount, ProfitAmount, Quantity, UnitPrice, Rating, IsWeekend, PaymentMethod, StoreKey, DateKey, CategoryKey

**Dimension Tables:**
- `DimDate`: Year, Month, Day  
- `DimStore`: StoreKey, City, Region  
- `DimProduct`: CategoryName, ProductName  
- `DimCustomer`: PaymentMethod, Rating  
- `DimTime`: IsWeekend, Hour

> The Star Schema enables fast, scalable, and flexible analytics across multiple dimensions.

---

## 📅 Time-Based Performance

<img width="480" height="240" alt="image" src="https://github.com/user-attachments/assets/4e619bf0-c319-4506-a9b2-621349bc7e65" />

**Insight:**  
Sales peak in December, but the real story is in the margins. Despite flat sales in 2023, profit surged—proof that Walmart shifted from volume to value.

| Year | Sales Amount | Profit Amount | Profit Margin |
|------|--------------|---------------|----------------|
| 2021 | $390K        | $120K         | 30.8%          |
| 2022 | $410K        | $140K         | 34.1%          |
| 2023 | $410K        | $218K         | 53.1%          |

**Recommendation:**  
- Forecast Q4 demand using historical spikes  
- Double down on margin-rich SKUs  
- Align staffing with seasonal surges

---

## 💳 Payment Method Preferences

<img width="480" height="240" alt="image" src="https://github.com/user-attachments/assets/6f9f82c2-c7bf-40ed-9d70-c94c96c90833" />

**Insight:**  
Cash remains dominant, but credit card usage is rising—likely tied to loyalty programs and digital channels.

| Payment Method | Sales Amount | % of Total |
|----------------|--------------|------------|
| Cash           | $484.39K     | 40.0%      |
| Credit Card    | $457.62K     | 37.8%      |
| Debit Card     | $268.4K      | 22.2%      |

**Recommendation:**  
- Promote digital payments to reduce cash handling costs  
- Tie credit card usage to loyalty rewards  
- Explore mobile payment options for younger demographics

---

## 📆 Weekend vs Weekday Dynamics

<img width="480" height="240" alt="image" src="https://github.com/user-attachments/assets/0e1568b4-f66d-4191-87e6-2e941217d0fb" />

**Insight:**  
Weekday sales dominate, accounting for nearly 68% of total revenue. Weekends show potential for leisure-driven purchases.

| Day Type | Sales Amount | Avg. Quantity | Avg. Profit |
|----------|--------------|---------------|-------------|
| Weekday  | $818.38K     | 7.2K          | $320K       |
| Weekend  | $392.96K     | 2.85K         | $158K       |

**Recommendation:**  
- Launch weekend flash sales and bundle offers  
- Optimize staffing based on weekday demand  
- Target weekend shoppers with lifestyle categories

---

## 🧴 Category Performance Breakdown

<img width="480" height="240" alt="image" src="https://github.com/user-attachments/assets/5de20607-3d55-46bf-8c5b-9ef51670cc18" />
<img width="480" height="240" alt="image" src="https://github.com/user-attachments/assets/3d471496-67cc-4225-aaaa-d118e83b63fe" />

**Insight:**  
Each category plays a distinct role in Walmart’s revenue mix.

| Category         | Avg. Unit Price | Profit Margin % | Quantity Sold |
|------------------|------------------|------------------|----------------|
| Food & Beverages | $12.50           | 28%              | 3.9K           |
| Health & Beauty  | $18.20           | 60%              | 1.2K           |
| Home & Kitchen   | $15.00           | 42%              | 2.1K           |
| Office Supplies  | $9.80            | 35%              | 1.5K           |
| Sports & Travel  | $22.40           | 48%              | 1.35K          |

**Recommendation:**  
- Upsell Health & Beauty with premium bundles  
- Improve Food margins via private-label strategy  
- Scale Home & Kitchen through seasonal campaigns

---

## 🗺️ Geographic Distribution

<img width="480" height="240" alt="image" src="https://github.com/user-attachments/assets/4eceb76f-eeb1-4754-96e0-4c9db9e40eda" />

**Insight:**  
Store density is highest in the Atlantic region, reflecting urban targeting. Sparse inland coverage reveals expansion opportunities.

**Recommendation:**  
- Expand into underserved regions with micro-format stores  
- Use regional performance data to tailor marketing  
- Consider mobile units or pop-up stores for rural outreach

---

## ⚖️ Sales vs Quantity Bubble Analysis

<img width="480" height="240" alt="image" src="https://github.com/user-attachments/assets/9f2164fd-6dad-4d34-89db-9aaf6ffefe5c" />

**Insight:**  
Food & Beverages = high volume, low value.  
Health & Beauty = low volume, high value.  
Home & Kitchen = balanced.

**Recommendation:**  
- Balance inventory across volume and margin  
- Align promotions with category behavior  
- Use bubble insights for pricing strategy

---

## 🖥️ Final DashBoard
<img width="1293" height="730" alt="image" src="https://github.com/user-attachments/assets/ed9bc281-e972-40c0-a609-8a3a9b8dd7ff" />

## 🔮 Strategic Outlook

**Predictions:**
- Profit-first strategy will continue  
- Digital payments will dominate  
- Premium categories will grow  
- Geographic expansion will accelerate  
- Personalization will become the norm

> This dashboard isn’t just a snapshot. It’s a telescope—it shows us what’s next.

---

## ✅ Final Takeaways

This dashboard, powered by a Star Schema data warehouse, enables fast, flexible, and insightful analysis. By combining transactional data with rich dimensions, we’ve uncovered patterns that inform inventory planning, promotional strategy, and regional growth.

> Crafted by Satyanarayana Nidamanauri 
> Data Analyst | Storyteller | Retail Strategist

