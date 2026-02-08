# 📊 Data Quality Impact Analysis on Retail Revenue

📌 Overview
In real-world analytics, data quality issues can significantly distort business decisions. This project analyzes a real transactional retail dataset (540k+ rows) to quantify how poor data quality affects key business metrics such as total revenue, average order value, and country-level performance.

Using Python and pandas, I:
- Audited the dataset for common data quality issues
- Defined and applied realistic data cleaning rules
- Recomputed core business KPIs before and after cleaning
- Quantified the business impact of bad data
- Visualized how conclusions change when data is properly cleaned

The results show that reported revenue was overstated by ~9% in the raw data and that customer spending behavior was significantly distorted.

🗂️ Dataset
Source: UCI Machine Learning Repository – Online Retail Dataset
Description:
Transactional data from a UK-based online retailer (2010–2011), including:
- Invoice numbers
- Product codes and descriptions
- Quantities and unit prices
- Customer IDs
- Countries

Size:
- 541,909 rows
- 8 original columns (+ derived Revenue column)

🎯 Business Questions
This project focuses on answering:
- How much do data quality issues distort reported revenue?
- How do returns, cancellations, missing IDs, and duplicates affect KPIs?
- Do strategic metrics (e.g., revenue by country, average order value) change after cleaning?
- What is the business risk of making decisions using raw, unvalidated data?

🔍 Data Quality Issues Identified
During the initial audit, the following issues were found:
- ~25% of rows missing CustomerID
- Negative quantities (returns)
- Zero or negative unit prices
- Canceled invoices (InvoiceNo starting with “C”)
- Duplicate records
- Date stored as string instead of datetime

These issues can:
- Overstate or understate revenue
- Distort customer behavior analysis
- Mislead market and product performance rankings

🧹 Cleaning Strategy
I applied the following rules to create a clean analytical dataset:
- Remove rows with missing CustomerID
- Remove rows with Quantity <= 0
- Remove rows with UnitPrice <= 0
- Remove canceled invoices (InvoiceNo starting with "C")
- Remove duplicate rows
- Recompute Revenue = Quantity × UnitPrice

📉 Data Reduction
- Original rows: 541,909
- Clean rows: 392,692

~27.5% of the data was removed due to quality issues.

📊 Business Metrics Compared
💰 Total Revenue
- Before cleaning: £9,747,747.93
- After cleaning: £8,887,208.89

Revenue was overstated by ~£860,539 (~8.8%) in the raw data.

🧾 Average Order Value (AOV)
- Before cleaning: £376.36
- After cleaning: £479.56

Cleaning reveals significantly higher true order values, showing that returns and invalid records were suppressing this KPI.

🌍 Top Countries by Revenue (After Cleaning)

- United Kingdom
- Netherlands
- EIRE
- Germany
- France

While rankings remain similar at the top, revenue values and lower-rank positions shift, showing that data quality can impact market prioritization decisions.

📈 Visual Analysis
Two key visualizations were created:
- Revenue by Country (Before vs After Cleaning)
- Shows how reported market performance changes after data validation
- Distribution of Order Values (Before vs After Cleaning)
- Demonstrates how dirty data distorts customer spending behavior
- These visuals reinforce the central finding: data quality materially changes business conclusions.

![Revenue by Country](visuals/revenue_by_country_before_after.png)
![Order Value Distribution](visuals/order_value_distribution_before_after.png)

🧠 Key Takeaways
- Over 27% of records contained issues that made them unsuitable for reliable analysis
- Raw data overstated revenue by nearly 9%
- Customer behavior metrics (AOV) were significantly distorted by poor data quality

Business decisions based on unclean data could lead to:
- Incorrect revenue forecasting
- Misallocation of resources by market
- Misinterpretation of customer value

🛠️ Tools & Technologies I used
- Python
- pandas
- vscode
- matplotlib
- Jupyter Notebook
