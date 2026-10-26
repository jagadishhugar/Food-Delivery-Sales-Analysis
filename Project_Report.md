# Food Delivery Sales Analysis: Customer and Sales Focus

**Course:** Data Analytics with Python  
**Project type:** Group assignment  
**Dataset:** `food_delivery_orders.csv`  
**Tools:** Python, Pandas, NumPy, Matplotlib, Jupyter Notebook

> **Academic data note:** The supplied dataset contains synthetic sample records created for demonstration. It does not represent a real food delivery company. The results below are reproducible for the included CSV, but must not be presented as real-world company findings.

## Abstract
This project applies data analytics with Python to study food delivery sales and customer behaviour. The analysis examines delivered revenue, order volume, average order value, monthly sales, city performance, customer segments, repeat purchases, cuisine categories, order channels, discounts, ratings, payment methods, cancellations, and refunds. Pandas is used to clean and summarize order records, NumPy supports numerical processing, and Matplotlib is used for visualization. The purpose is to turn transaction data into understandable evidence that can support customer retention, marketing, and operational decisions.

## 1. Introduction
Food delivery businesses generate transaction data every time a customer places an order. However, raw order records do not automatically explain which customers are valuable, which locations perform well, or whether customers return after their first purchase. A structured analysis is needed to measure sales performance and understand customer behaviour.

This project focuses on two connected areas:
- **Sales:** revenue, order volume, AOV, time trends, city performance, cuisine and channel contribution.
- **Customers:** customer segments, spending patterns, repeat orders, and possible customer-experience signals.

The analysis uses an educational sample dataset. It demonstrates a repeatable workflow rather than making claims about an actual company.

## 2. Problem Statement
The project aims to analyze food delivery orders to identify sales patterns and customer behaviours that can inform practical business recommendations. It asks: how much revenue comes from delivered orders; which periods, cities, segments, cuisines, and channels contribute most; how many customers return; and what do order statuses, ratings, and discount levels reveal?

## 3. Objectives
1. Load and inspect the dataset using Pandas.
2. Check missing values, duplicate order IDs, and data types.
3. Calculate delivered revenue, delivered orders, AOV, unique customers, repeat customers, cancellation rate, and refund rate.
4. Compare monthly sales and city-wise performance.
5. Analyze customer segments, top customers, and repeat-purchase frequency.
6. Compare cuisine categories, order channels, payment methods, discounts, and ratings.
7. Visualize key findings using Matplotlib.
8. Make recommendations grounded in the results and identify limitations.

## 4. Dataset Description
The CSV includes 600 order records and 17 columns. One row represents one order.

| Field | Description |
|---|---|
| `order_id` | Unique order identifier |
| `order_date` | Order date |
| `customer_id` | Artificial customer identifier |
| `city` | City associated with the order |
| `customer_segment` | New, Regular, or Premium |
| `order_channel` | App, Website, or Phone |
| `cuisine` | Cuisine category |
| `quantity` | Number of items |
| `unit_price_inr` | Price per item in rupees |
| `discount_pct` | Discount as a decimal fraction |
| `discount_amount_inr` | Discount value |
| `delivery_fee_inr` | Delivery fee |
| `total_amount_inr` | Final order amount after discount plus delivery fee |
| `payment_method` | Payment method |
| `rating` | Customer rating from 1 to 5 |
| `order_status` | Delivered, Cancelled, or Refunded |

### Data scope and assumptions
- The dataset is synthetic and is intended for classroom practice.
- Only orders with status `Delivered` are included in sales revenue and AOV calculations.
- All statuses are included when calculating cancellation and refund rates.
- Revenue is not profit because product costs, restaurant commissions, delivery costs, and marketing costs are unavailable.

## 5. Tools and Technologies
- **Python:** core programming language.
- **Pandas:** CSV input, cleaning, filtering, grouping, pivoting, and aggregation.
- **NumPy:** numerical calculations and array-based operations.
- **Matplotlib:** line, bar, and histogram visualizations.
- **Jupyter Notebook:** combines code, explanation, tables, and charts.

Install dependencies using `pip install pandas numpy matplotlib jupyter`.

## 6. Methodology
The project follows these stages:
1. **Load data:** read the CSV and parse the date column.
2. **Inspect:** review shape, sample rows, data types, missing values, and duplicate order IDs.
3. **Prepare:** remove duplicate order IDs if present, trim whitespace from categorical values, and create a month field.
4. **Define analysis population:** create a delivered-orders subset for sales analysis.
5. **Calculate KPIs:** summarize revenue, order volume, AOV, unique customers, repeat customers, cancellations, and refunds.
6. **Explore patterns:** group by month, city, segment, customer, cuisine, channel, discount, rating, and payment method.
7. **Visualize:** create charts that make trends and comparisons easier to interpret.
8. **Interpret and recommend:** write findings from observed outputs and identify data needed for stronger decisions.

## 7. Key Metric Definitions
- **Delivered revenue:** sum of `total_amount_inr` for delivered orders.
- **Delivered orders:** count of orders with status `Delivered`.
- **Average order value (AOV):** delivered revenue divided by delivered order count.
- **Unique delivered customers:** distinct customers with at least one delivered order.
- **Repeat customer:** customer with at least two delivered orders.
- **Repeat-customer percentage:** repeat customers divided by unique delivered customers, multiplied by 100.
- **Cancellation rate:** cancelled orders divided by all orders, multiplied by 100.
- **Refund rate:** refunded orders divided by all orders, multiplied by 100.

## 8. Results for the Included Sample Dataset
The values below are calculated directly from the included CSV and should match when the notebook is run against that same file.

| Metric | Result |
|---|---:|
| Total orders | 600 |
| Delivered orders | 551 |
| Delivered revenue | ₹425,294.00 |
| Average order value | ₹771.86 |
| Unique customers with delivered orders | 174 |
| Repeat customers (2+ delivered orders) | 147 |
| Repeat customers as % of unique delivered customers | 84.48% |
| Cancellation rate | 6.17% |
| Refund rate | 2.00% |

### Highest-contributing groups in the included sample
| Analysis | Highest group | Delivered revenue |
|---|---|---:|
| Month | 2025-02 | ₹49,755.00 |
| City | Udupi | ₹98,892.00 |
| Customer segment | Regular | ₹223,896.00 |
| Cuisine | Italian | ₹82,524.50 |
| Order channel | App | ₹317,663.50 |

These are descriptive results from a synthetic dataset. They do not establish why a group performs well, nor do they predict future performance.

## 9. Analysis and Discussion

### 9.1 Sales performance
The KPI table provides a baseline for order volume and delivered revenue. AOV helps distinguish between a high order count and high spending per order. When reporting revenue, state the population used: in this project, cancelled and refunded orders are excluded from delivered revenue.

### 9.2 Monthly sales trend
Monthly grouping shows how revenue and order volume change over the year. A peak in revenue can reflect more orders, larger orders, or both. The order and customer counts should be checked alongside revenue before explaining a peak. A single year of synthetic data is not enough to establish a reliable seasonal pattern.

### 9.3 City-wise performance
City comparisons include revenue, order count, AOV, and unique customers. The city with the highest revenue may simply have more orders. AOV and customer count provide additional context. City-specific promotions should be tested rather than assumed to work based on revenue alone.

### 9.4 Customer segment analysis
Segment analysis compares New, Regular, and Premium customers. Total revenue measures overall contribution, while AOV and customer count help explain that contribution. The label “Premium” should not be treated as proof of profitability; actual margin and retention data would be needed.

### 9.5 Top customers and repeat purchasing
Ranking customers by delivered spend identifies the highest-spending IDs in the sample. The order-frequency distribution indicates whether customers commonly place one order or return several times. Repeat purchasing can be encouraged with reorder reminders and loyalty programs, but campaign success should be measured using repeat rate and incremental revenue.

### 9.6 Cuisine and ordering channel
Cuisine summaries identify categories with higher revenue or order counts. Channel summaries compare app, website, and phone orders. Since order volumes may differ substantially, both total revenue and AOV should be reviewed. The data does not include channel acquisition cost, so it cannot determine which channel is most profitable.

### 9.7 Discounts and customer experience
Discount-level comparisons show order count, revenue, and AOV by discount rate. A larger discount may be associated with more orders, but this does not prove that the discount caused the increase or improved profit. Ratings can help describe customer feedback, while cancellation and refund rates indicate areas for further investigation. Reason codes and delivery-time information are needed to explain failed orders.

## 10. Recommendations
1. **Improve first-to-second-order conversion:** send timely reorder reminders to customers with one delivered order.
2. **Reward repeat and high-value customers:** create loyalty tiers based on observed frequency and spend; monitor the cost of rewards.
3. **Use city-level campaigns:** compare revenue, AOV, and customer count before allocating local marketing budgets.
4. **Promote cuisines using evidence:** feature categories with strong performance and run controlled tests for underperforming categories.
5. **Test discount effectiveness:** compare orders and AOV across discount levels, and add cost/margin data before judging profitability.
6. **Reduce cancellations and refunds:** collect structured reasons such as payment failure, customer cancellation, restaurant delay, and delivery issues.
7. **Measure retention over time:** add customer signup date and acquisition source to support cohort analysis.
8. **Track profit alongside revenue:** collect food costs, restaurant commission, delivery expense, and marketing spend to estimate contribution margin.
9. **Improve service quality analysis:** add promised and actual delivery times and link them to ratings, repeat orders, and refunds.

## 11. Limitations
- The dataset is synthetic and does not represent a real company.
- One record represents an order, not an individual item-level transaction.
- There are no restaurant IDs, delivery times, cancellation reasons, customer signup dates, or acquisition costs.
- Profit, customer lifetime value, and marketing return on investment cannot be reliably calculated.
- The observed associations do not prove causation.
- Findings may change if the dataset is replaced or updated.

## 12. Conclusion
The project demonstrates a complete introductory data analytics workflow for food delivery sales and customer behaviour. Python makes it possible to clean data, calculate meaningful KPIs, compare customer groups, and visualize sales trends. The results can guide hypotheses about customer retention, location-based marketing, cuisine promotion, and order reliability. For real business decisions, the analysis should be repeated on validated company data and extended with costs, delivery performance, and customer-history fields.

## 13. Suggested Group Work Distribution
| Member | Responsibility | Expected deliverable |
|---|---|---|
| Member 1 | Dataset description, import, and data quality | Data profile and cleaning explanation |
| Member 2 | KPIs, monthly trends, and city analysis | KPI table and sales charts |
| Member 3 | Customer segments, top customers, repeat purchases | Customer analysis tables and insights |
| Member 4 | Cuisine/channel analysis, report, and presentation | Findings, recommendations, and slides |

## Appendix A: Expected Notebook Outputs
The notebook includes expected-output notes after each code section. On the included CSV, the notebook should show:
- dataset shape `(600, 16)`;
- a missing-value table and duplicate-order count;
- KPI summary table;
- monthly sales table and two charts;
- city, segment, customer, cuisine, channel, discount, rating, payment, and status summaries;
- city-by-segment pivot table and order-count cross-tabulation.

Exact tables should be copied from the executed notebook if a different CSV is used.
