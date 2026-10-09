# 📡 Customer Retention Analytics | Power BI Dashboard

**Why are telecom customers leaving, who is leaving, and what does it cost?**
An end-to-end Power BI project: raw customer data → Power Query → DAX measures → a two-page interactive dashboard.

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-%20Measures-0078D4?style=for-the-badge)
![Power Query](https://img.shields.io/badge/Power%20Query-M-217346?style=for-the-badge)

---

## 📸 Dashboard Preview

**Page 1: Executive Overview**

![Customer Retention Analytics: Executive Overview page](Dashboard%201.png)

**Page 2: Customer Retention Analysis**

![Customer Retention Analytics: Customer Retention Analysis page](Dashboard%202.png)

---

## 1. 🔍 Overview

I built this dashboard to analyse **customer churn and retention for a telecom provider** in **California**. The data covers **7,043 customers** over one quarter (Q3): their contracts, services, charges, satisfaction scores and the reasons churned customers gave for leaving.

The report has **2 pages**:

| Page | What it shows |
|---|---|
| **Executive Overview** | Headline KPIs, customer status, churn by contract and tenure, revenue lost, top cities by churn |
| **Customer Retention Analysis** | CLTV, charges, satisfaction and tenure KPIs, internet service performance, churn lifecycle, churn drivers and reasons |

Both pages share slicers for **Contract, Payment Method, Tenure Group, Offer and Internet Type**, so any customer group can be explored in one click.

---

## 2. ⚠️ Business Problems

The company was losing customers and revenue, but had no clear view of where the problem was. Management needed answers to:

- 📉 **How big is the problem?** What share of customers is churning, and how much revenue leaves with them?
- 👥 **Who is churning?** Which contracts, services, tenure groups and customer profiles churn the most?
- ❓ **Why are they leaving?** What are the main churn categories and reasons?
- ⏳ **When do they leave?** At what point in the customer lifecycle are customers lost?
- 📍 **Where are they leaving?** Which cities have the highest churn?
- 🛡️ **What keeps customers?** Do add-on services, offers, referrals and payment methods reduce churn?

---

## 3. 🎯 Objectives

1. Measure the **churn rate, retention rate and revenue lost** to churn.
2. Identify the **customer segments** with the highest churn (contract, tenure, internet type, demographics).
3. Find the **main reasons** customers leave.
4. Locate the **cities** where churn is concentrated.
5. Flag **active customers at high risk** of churning.
6. Give management a **clear, interactive dashboard** and practical **retention recommendations**.

---

## 4. 🗂️ Dataset

| Item | Details |
|---|---|
| **Source** | kaggle, one CSV file (`telcoy.csv`) |
| **Rows** | **7,043** (one row per customer) |
| **Columns** | **61** |
| **Coverage** | One quarter (Q3), customers across 1,106 cities in California |
| **Data model** | 2 tables: `telcoy` (customer data) and `Measures Table` (40 DAX measures) |

**What the 61 columns cover**

| Column group | Examples |
|---|---|
| 👤 Demographics | Gender, Age, Senior Citizen, Married, Dependents |
| 📍 Location | City, Zip Code, Latitude, Longitude, Population |
| 📄 Account | Tenure in Months, Contract, Offer, Payment Method, Paperless Billing |
| 📶 Services | Phone, Internet Type, Online Security, Premium Tech Support, Streaming, Unlimited Data |
| 💵 Billing | Monthly Charge, Total Charges, Total Refunds, Total Revenue |
| 🚪 Outcome | Customer Status (Stayed / Joined / Churned), Churn Category, Churn Reason, Churn Score, CLTV, Satisfaction Score |
| 🧩 Segmentation | Tenure Group, Satisfaction Band, Add-on Services Count, Monthly Charge Tier, CLTV Tier, Churn Flag, High Churn Risk |

---

## 5. 🛠️ Methodology

**Step 1: Data preparation (Power Query)**
- Imported the CSV, promoted headers and set an explicit data type for all 61 columns.
- Used segmentation columns to slice the analysis: tenure groups (0–12, 13–24, 25–48, 49–72 months), satisfaction bands, add-on count, monthly charge tiers, CLTV quartiles, a churn flag and a High Churn Risk flag (active customers with a churn score of 80+).

**Step 2: Data validation**
- 7,043 rows = 7,043 unique Customer IDs, so no duplicate customers.
- No missing values in any analysis column.
- Customer status reconciles: 4,720 Stayed + 454 Joined + 1,869 Churned = 7,043.
- Churn count matches across three columns (Customer Status, Churn Label, Churn Flag): **1,869** each.

**Step 3: Data modelling**
- Kept all ** DAX measures** in a dedicated **Measures Table**, separate from the data.
- Added sort-by columns so Tenure Group and Contract always display in logical order.

**Step 4: DAX measures**
- Core KPIs: Total Customers, Total Churned Customers, Churn Rate %, Retention Rate %, Active Customers.
- Revenue: Total Revenue, Revenue Lost From Churn, Revenue Loss %, Average CLTV, Avg Monthly Charges.
- Drivers: Contract Churn Rate, Early Churn Rate, Fiber Churn Rate, Competitor Churn %, Pricing Churn %, Support Related Churn.
- Risk and location: High Risk Active Customers, Active Risk Profile %, City Churn Rate, City Churn Rank.

```dax
Churn Rate % = DIVIDE ( [Total Churned Customers], [Total Customers], 0 )

Early Churn Rate = DIVIDE ( [Early Churn Customers], [Total Churned Customers] )
```

**Step 5: Dashboard design**
- Built the two report pages with KPI cards, 100% stacked, bar, column, donut and scatter charts, slicers and tooltips.
- Checked every KPI card against totals calculated directly from the source file.

---

## 6. 📊 Key Metrics

| KPI | Value |
|---|---|
| 👥 Total Customers | **7,043** |
| 🚪 Churned Customers | **1,869** |
| 📉 Churn Rate | **26.5%** |
| ✅ Retention Rate | **73.5%** |
| 💸 Monthly Charges Lost to Churn | **$139,131** (30.5% of monthly billing, ≈ **$1.67M a year**) |
| 💰 Total Revenue (lifetime) | **$21.37M** |
| 🔻 Lifetime Revenue from Churned Customers | **$3.68M** (17.2%) |
| 💳 Average Monthly Charge | **$64.76** |
| 🏆 Average Customer Lifetime Value (CLTV) | **$4,400** |
| ⏱️ Average Tenure | **32.4 months** |
| ⭐ Average Satisfaction Score | **3.24 / 5** |
| 🚨 High-Risk Active Customers | **96** (1.9% of 5,174 active) |

---

## 7. 🧰 Skills and Tools

| Tool / Skill | How I used it |
|---|---|
| **Power BI Desktop** | Report design, KPI cards, charts, slicers, tooltips |
| **Power Query (M)** | CSV import, headers, data types |
| **Data Modelling** | Dedicated measures table, sort-by columns, segmentation columns |
| **DAX** | CALCULATE, DIVIDE, DISTINCTCOUNT, COUNTROWS, RANKX, ALLSELECTED, ISINSCOPE, SWITCH |
| **Data Validation** | Duplicate and null checks, reconciling KPIs to the source |
| **Analysis** | Churn and retention rates, tenure (lifecycle) analysis, segmentation, revenue impact, root-cause analysis |
| **Data Storytelling** | Turning churn numbers into clear retention actions for management |

---

## 8. 💡 Insights and Findings

**1. One in four customers left.**
1,869 of 7,043 customers churned (**26.5%**), taking **$139,131 a month** with them: **30.5%** of monthly billing, about **$1.67M a year**. Churned customers paid more per month than those who stayed ($74.44 vs $62.98).

**2. Contract type is the strongest driver.**

| Contract | Customers | Churn Rate |
|---|---|---|
| Month-to-Month | 3,610 | **45.8%** |
| One Year | 1,550 | 10.7% |
| Two Year | 1,883 | 2.5% |

Month-to-month customers make up **88.6%** of all churners.

**3. Churn happens early.**
**55.5%** of churners (1,037) left within their **first 12 months**. Churn falls from **47.4%** (0–12 months) to **9.5%** (49–72 months).

**4. Fiber Optic is the problem product.**
Fiber customers churn at **40.7%** (vs 18.6% for DSL) and account for **78.2%** of monthly revenue lost. Fiber on a month-to-month contract churns at **58.8%**.

**5. Competitors, not price, win the customers.**

| Churn Category | Share of Churners |
|---|---|
| Competitor | **45.0%** |
| Attitude | 16.8% |
| Dissatisfaction | 16.2% |
| Price | 11.3% |
| Other | 10.7% |

Top reasons: competitor had better devices (16.7%) and made a better offer (16.6%). Support staff attitude or expertise drove **263** customers away (14.1%).

**6. Add-ons and loyalty protect retention.**
- Online Security: 14.6% churn with it vs 31.3% without.
- Premium Tech Support: 15.2% vs 31.2%.
- Churn falls from **43.2%** with one add-on to **5.1%** with all seven.
- Credit card payers churn at **14.5%**, vs 34.0% (bank withdrawal) and 36.9% (mailed check).
- **Offer E** has the highest churn (**52.9%**); Offer A the lowest (6.7%).
- Senior citizens churn at **41.7%**, vs 23.6% for everyone else.

**7. San Diego is a hotspot.**
San Diego churns at **64.9%** and alone accounts for **9.9%** of all churn. With nearby Fallbrook and Temecula, the area lost **233 of 366** customers.

**8. Satisfaction is a lagging signal.**
Every customer who scored 1 or 2 churned, and none who scored 4 or 5 did. The score explains churn well, but it looks like it is captured at the point of leaving, so it is not an early warning.

---

## 9. ✅ Recommendations

1. 📝 **Move month-to-month customers onto contracts.** Offer discounts, device deals or bonus data for switching to a 1- or 2-year plan, starting with Fiber month-to-month customers (58.8% churn).
2. 🤝 **Build a first-year onboarding programme.** Check-ins at months 1, 3 and 6, welcome offers and early service reviews, since 55.5% of churners leave in year one.
3. 🌐 **Fix the Fiber Optic experience.** Review speed, reliability and pricing against competitors; Fiber drives 78.2% of lost monthly revenue.
4. 📱 **Compete on devices and offers.** Run a device-upgrade programme and match competitor offers for at-risk customers.
5. 🔒 **Bundle protective add-ons.** Include Online Security and Premium Tech Support free or discounted in the first year.
6. 🎧 **Train and monitor support teams.** Add quality scoring and coaching for support calls.
7. 📍 **Investigate San Diego** and launch a regional retention campaign there.
8. 💳 **Review Offer E** and promote **credit card autopay**.
9. 🚨 **Contact the 96 high-risk active customers now** with personal retention calls and targeted offers.
10. 👴 **Support senior citizens** with simpler plans and dedicated help.

---

## 👤 Author

**Tajudeen Gbenga Rabiu** | Data Analyst · Power BI · SQL · Python · Excel

- 💼 LinkedIn: [linkedin.com/in/tajudeen-rabiu-data](https://www.linkedin.com/in/tajudeen-rabiu-data)
- 📧 Email: [rabiutajudeen77@gmail.com](mailto:rabiutajudeen77@gmail.com)

⭐ If you found this project useful, please star the repository.
