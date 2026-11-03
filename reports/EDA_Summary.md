
# Exploratory Data Analysis Summary
## Online Retail Dataset

## 1. Project Overview

This report summarizes the key findings from an Exploratory Data Analysis (EDA) of the Online Retail dataset.

The analysis focuses on understanding customer behavior, product performance, sales trends over time, geographical distribution, and unit price patterns.

**Dataset Source:** [UCI Machine Learning Repository - Online Retail](https://archive.ics.uci.edu/dataset/352/online+retail)

## 2. Dataset Overview

| Metric | Value |
|---|---:|
| Total Records | 541,909 |
| Available Features | 6 |
| Unique Customers | 4,372 |
| Unique Product Descriptions | 4,077 |
| Date Range | Dec 2010 – Dec 2011 |
| Countries | Multiple |

### Available Features

- `Description`: Product description.
- `Quantity`: Number of units in each record.
- `InvoiceDate`: Date and time of the transaction.
- `UnitPrice`: Price per unit.
- `CustomerID`: Customer identifier.
- `Country`: Customer's country.

## 3. Data Quality Findings

The initial inspection revealed the following data quality issues:

| Feature | Finding |
|---|---|
| CustomerID | 135,080 missing values (24.93%) |
| Description | 1,454 missing values |
| InvoiceDate | No missing values after datetime conversion |
| UnitPrice | 2 negative values and 2,515 zero-price records |

Additional observations:

- Unit prices contain unusually high values.
- Some records represent fees, postage, or manual adjustments rather than ordinary product sales.
- Negative quantities may represent returns or adjustments and should not automatically be treated as errors.

## 4. Customer Analysis

- The dataset contains 4,372 unique identified customers.
- Customer activity is highly right-skewed, with some customers contributing considerably more records than others.
- Customers with the highest number of records are not necessarily the highest-spending customers.
- Customer spending was calculated using the sum of `LineTotal` for each customer.

### Top Spending Customers

| Customer ID | Total Spending |
|---:|---:|
| 14646 | 279,489.02 |
| 18102 | 256,438.49 |
| 17450 | 187,482.17 |
| 14911 | 132,572.62 |
| 12415 | 123,725.45 |

**Key Insight:** Customer activity and spending are different dimensions. A high number of product-line records does not necessarily indicate the highest total spending.

## 5. Product Analysis

The product analysis identified 4,077 unique product descriptions.

### Top Products by Quantity Sold

| Product | Quantity Sold |
|---|---:|
| PAPER CRAFT, LITTLE BIRDIE | 80,995 |
| MEDIUM CERAMIC TOP STORAGE JAR | 78,033 |
| WORLD WAR 2 GLIDERS ASSTD DESIGNS | 55,047 |
| JUMBO BAG RED RETROSPOT | 48,478 |
| WHITE HANGING HEART T-LIGHT HOLDER | 37,895 |

### Top Products by Revenue

| Product | Revenue |
|---|---:|
| DOTCOM POSTAGE | 206,248.77 |
| REGENCY CAKESTAND 3 TIER | 174,484.74 |
| PAPER CRAFT, LITTLE BIRDIE | 168,469.60 |
| WHITE HANGING HEART T-LIGHT HOLDER | 106,292.77 |
| PARTY BUNTING | 99,504.33 |

### Low-Selling Products

- 424 product descriptions (10.4%) recorded total sales quantities of 10 units or fewer.
- The 10th percentile of product sales quantity was 10 units.
- 69 product descriptions recorded only one unit sold.

**Key Insights:**

- Product quantity and revenue rankings differ because products have different unit prices.
- PAPER CRAFT, LITTLE BIRDIE ranked first by quantity but third by revenue.
- DOTCOM POSTAGE ranked first by revenue, demonstrating that some high-revenue entries are service-related rather than ordinary products.
- Low sales volume does not necessarily indicate poor product performance.

## 6. Time-Based Analysis

The analysis covered records from December 1, 2010, to December 9, 2011.

### Monthly Trends

- November 2011 recorded the highest monthly revenue and quantity.
- Revenue and quantity increased noticeably during September–November 2011.
- December 2011 showed a sharp decline, but the month is incomplete because the dataset ends on December 9.
- Monthly revenue growth was particularly strong in May (+46.66%) and September (+49.37%).

### Daily and Hourly Trends

- Thursday recorded the highest average daily revenue among observed weekdays.
- Sunday recorded the lowest average daily revenue among observed weekdays.
- No Saturday observations were available in the daily revenue aggregation.
- 12 PM recorded the highest total revenue among the observed hours.
- Revenue activity was concentrated mainly between 10 AM and 3 PM.

**Key Insight:** Sales activity varied considerably across months and hours. However, the available period is insufficient to establish reliable recurring seasonal patterns.

## 7. Geographical Analysis

The geographical analysis revealed a strong concentration of sales activity in the United Kingdom.

### Top Countries by Quantity

| Country | Total Quantity | Quantity Share |
|---|---:|---:|
| United Kingdom | 4,263,829 | 82.37% |
| Netherlands | 200,128 | 3.87% |
| EIRE | 142,637 | 2.76% |
| Germany | 117,448 | 2.27% |
| France | 110,480 | 2.13% |

### Key Findings

- The United Kingdom accounts for 91.43% of transaction records and 82.37% of total quantity.
- The Netherlands ranks second in total quantity despite representing only 0.44% of transaction records.
- Germany and France have more records than the Netherlands but lower total quantities.
- Differences between record shares and quantity shares suggest variations in the average quantity recorded per product line across countries.

**Key Insight:** Sales activity is heavily concentrated in the United Kingdom, while other countries contribute relatively small shares.

## 8. Unit Price Analysis

The unit price distribution is strongly right-skewed.

### Descriptive Statistics

| Statistic | Value |
|---|---:|
| Mean | 4.61 |
| Standard Deviation | 96.76 |
| Median | 2.08 |
| 25th Percentile | 1.25 |
| 75th Percentile | 4.13 |
| 95th Percentile | 9.95 |
| 99th Percentile | 18.00 |
| Minimum | -11,062.06 |
| Maximum | 38,970.00 |

### Unusual Values

- 2 records contain negative unit prices.
- 2,515 records have zero unit prices.
- 4,790 records have unit prices above the 99th percentile threshold.
- Some extreme values are associated with `AMAZON FEE`, `POSTAGE`, `Manual`, and `Adjust bad debt`.
- Some high-priced records represent actual products and should not automatically be removed.

**Key Insight:** Unusual prices require contextual investigation. Statistical outliers are not necessarily invalid observations.

## 9. Limitations

Several limitations affected the scope of the analysis:

- The available dataset version contains only six features and does not include `InvoiceNo` or `StockCode`.
- Invoice-level analysis and reliable purchase frequency calculations could not be performed.
- Cancellation identification could not be reliably performed using invoice identifiers.
- Product grouping relied on descriptions, which may contain inconsistent naming.
- Some revenue calculations include negative quantities and special accounting or service-related records.
- December 2011 is incomplete.
- The dataset covers approximately one year, limiting the ability to establish long-term seasonal patterns.

## 10. Conclusion

This EDA explored customer behavior, product performance, temporal sales patterns, geographical distribution, and unit price characteristics.

The analysis revealed that:

- Sales activity is highly concentrated in the United Kingdom.
- Product popularity does not necessarily correspond to revenue contribution.
- Customer activity and spending are not equivalent.
- Sales patterns vary across months and hours.
- Unit price data contains unusual values that require context-aware treatment.

Overall, this project demonstrates the importance of combining statistical analysis, visualization, and business understanding to extract meaningful insights from real-world retail data.

**The findings provide a foundation for further data analysis and future preprocessing tasks.**
