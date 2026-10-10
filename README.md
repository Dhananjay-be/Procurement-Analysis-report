# Project Report: Procurement & Supplier Performance Analytics Dashboard
# 1. Project Overview
This project involved the end-to-end analysis of a procurement dataset containing 777 purchase orders. 
The primary objective was to develop an interactive Excel dashboard to provide actionable business insights into procurement spend, supplier performance, cost savings, and data quality. 
The analysis covers a three-year period (2022-2024) and evaluates performance across five key suppliers and five primary item categories.
The project demonstrates the ability to transform raw, and often flawed, transactional data into a strategic tool for decision-makers in a procurement or supply chain function.
# 2. Business Problem & Objectives
The procurement department lacked a consolidated, reliable view of its operational and financial performance. Key questions from stakeholders included:
•	Cost Efficiency: Are we successfully negotiating cost savings, and which suppliers/categories are driving them?
•	Supplier Management: Which suppliers are the most reliable in terms of on-time delivery, compliance, and quality?
•	Spend Visibility: Where is the organization's money being spent? Are there patterns in procurement activity over time?
•	Data Integrity: How reliable is the underlying procurement data for strategic decision-making?
The objective was to build a dashboard that could answer these questions and serve as a single source of truth for procurement KPIs.
# 3. Dataset & Tools
•	Dataset: Procurement KPI Analysis Dataset.xlsx containing 777 records and 19 columns. Key fields included PO_ID, Supplier, Order_Date, Delivery_Date, Order_Status, Quantity, Unit_Price, Negotiated_Price, Defective_Units, and Compliance.
•	Tools: Microsoft Excel (Power Query for data transformation, PivotTables for aggregation, PivotCharts for visualization, and advanced formulas for KPI calculation). The report also leveraged data quality auditing techniques within Excel.
# 4. Methodology & Data Quality Audit
A critical first step was a data quality audit, which uncovered several inconsistencies that needed to be addressed before reliable analysis could be performed.
•	Derived Columns: Created Lead_Time, Total_Spend, Original_Spend, Cost_Savings, and Defect_Rate using formulas.
•	Data Inconsistency 1: Order Status vs. Delivery Date: Identified significant logical flaws where orders were marked as Cancelled, Pending, or Partially Delivered but still had a Delivery_Date recorded. Conversely, many orders marked Delivered were missing a Delivery_Date. A Data_Quality_Flag column was created to identify these "Status-Date Conflicts."
•	Data Inconsistency 2: Quality Data for Undelivered Orders: Observed that non-delivered orders (Cancelled, Pending) had Defective_Units and, by extension, a calculated Defect_Rate. This is illogical, as defects can only be measured for products that have been received.
•	Data Inconsistency 3: Invalid Category: Discovered a category named "del" in the Item_Category column, which is not a valid procurement category. This was traced to be a stale item in a PivotTable cache, not an error in the raw data.
•	Issue Resolution: A step-by-step guide was provided to resolve the invalid "del" category by clearing the PivotTable cache (changing "Number of items to retain per field" to "None"). This showcases a deep understanding of Excel's internal workings.
This rigorous validation process ensures the final dashboard's insights are built on a foundation of clean, logical data.
# 5. Key Performance Indicators (KPIs) & Calculations
A set of core KPIs was established to measure performance:
•	Total Negotiated Spend: SUM(Total_Spend) = $45,373,696.39
•	Total Cost Savings: SUM(Original_Spend) - SUM(Total_Spend) = $3,931,126.47
•	Savings Percentage: Total Cost Savings / Total Original Spend = 7.97%
•	Total Defective Units: SUM(Defective_Units) = 47,949
•	Overall Defect Rate: SUM(Defective_Units) / SUM(Quantity) = 5.64%
•	Supplier Compliance Rate: COUNT(Compliance = "Yes") / Total Orders = 82.4%
•	On-Time Delivery Rate (for Delivered Orders): COUNT(Lead_Time <= 10) / COUNT(Order_Status = "Delivered").
# 6. Dashboard Structure & Business Insights
The dashboard is organized into thematic sections to provide a clear narrative.
a. Executive Summary (High-Level KPIs)
An at-a-glance view of the most critical metrics for senior management.
•	Total Spend: $45.4M
•	Total Savings: $3.9M (8.0%)
•	Compliance Rate: 82.4%
•	Overall Defect Rate: 5.6%
•	Pending Order Rate: 10.4%
b. Spend & Savings Analysis
This section addresses the question: "Are we getting price savings?"
•	Spend by Category: The top spending categories are MRO ($10.1M)** , **Office Supplies ($10.0M) , and Beta_Supplies ($9.9M) . This insight allows for strategic category management.
•	Savings by Supplier: Beta_Supplies generated the highest total savings ($889K), while **Gamma_Co** had the lowest ($725K). This highlights opportunities for negotiating better terms with lower-performing suppliers.
•	Spend Trends: Analysis of spend by year shows a significant increase in **2023 ($23.7M)** compared to 2022 ($21.5M), indicating business growth or increased procurement activity.
c. Supplier Performance Analysis
This section addresses: "Which suppliers/categories matter most?" and "Are they meeting expectations?"
•	Delivery Performance: A PivotTable comparing Supplier against Average Lead_Time shows Gamma_Co has the fastest average lead time (10.2 days), while Beta_Supplies has the slowest (11.3 days).
•	Quality Performance: Epsilon_Group has an exceptionally low defect count (4,682 units), whereas Delta_Logistics (19,678 units) and Beta_Supplies (13,838 units) are the primary sources of defective products. This is a critical finding for quality control.
•	Compliance: While the overall compliance rate is high, the PivotTable Count of Supplier vs. Compliance reveals that Delta_Logistics accounts for 67 of the 137 non-compliant orders, making it a key area for supplier development.
d. Order Status & Operational Analysis
This section addresses: "Are orders being delivered properly?"
•	Order Status Breakdown: Of the 777 orders, 560 (72.1%) were successfully Delivered. However, 81 (10.4%) are Pending, 73 (9.4%) are Partially Delivered, and 63 (8.1%) are Cancelled.
•	Supplier Reliability: Delta_Logistics has the highest number of cancelled orders (16), while Beta_Supplies has the most pending orders (19). This provides a clear metric for supplier reliability beyond just lead time.
e. Time-Series Trends
Business question: Are procurement patterns changing over time?
This analysis uses Order_Date to examine monthly and quarterly procurement patterns. Negotiated order value is calculated as Quantity × Negotiated_Price, while the average negotiated price represents the arithmetic mean of Negotiated_Price across purchase orders in each period. These measures help distinguish changes in procurement value from changes in average unit prices.
Quarterly Trend Analysis
Quarter	Purchase Orders	Negotiated Order Value	Average Negotiated Price
2022 Q1	99	₹55.07 L	₹48.21
2022 Q2	94	₹46.67 L	₹49.07
2022 Q3	113	₹57.99 L	₹52.96
2022 Q4	90	₹54.88 L	₹53.26
2023 Q1	97	₹67.95 L	₹59.87
2023 Q2	79	₹46.18 L	₹56.71
2023 Q3	104	₹66.07 L	₹53.88
2023 Q4	99	₹57.24 L	₹55.62
2024 Q1*	2	₹1.69 L	₹66.52
2024 Q1 contains only two January purchase orders and does not represent a complete quarter.
The average negotiated price increased from ₹50.92 in 2022 to ₹56.46 in 2023, an increase of approximately 10.9%. However, the quarterly pattern was not consistently upward. Prices increased throughout 2022 and reached ₹59.87 in 2023 Q1, before declining in Q2 and Q3 and rising modestly in Q4.
Negotiated order value increased from ₹2.15 crore in 2022 to ₹2.37 crore in 2023, a rise of approximately 10.6%. Aggregate ordered quantity changed by only 0.3%, from 423,314 to 424,677. This suggests that the increase in order value was not explained by a substantial rise in aggregate quantity alone.
Nevertheless, these findings do not establish inflation. Changes in supplier mix, product categories and the types of goods purchased may also affect the average negotiated price. A like-for-like comparison of the same products would be required to isolate price changes more reliably.
Monthly Procurement Spend Patterns
The highest monthly negotiated order values include:
Month	Negotiated Order Value
March 2022	₹25.93 L
August 2022	₹23.29 L
March 2023	₹27.44 L
July 2023	₹23.66 L
November 2023	₹25.84 L
March was the highest-spend month in both 2022 and 2023. August recorded relatively high spending in 2022, while November was another notable peak in 2023. These observations suggest that monthly procurement activity fluctuates and that certain periods warrant closer investigation.
However, the dataset does not contain budget calendars, purchasing targets or operational explanations for these peaks. It would therefore be speculative to attribute March spending to year-end budget utilisation or to conclude that August represents a recurring business cycle.
Business Implications and Recommendations
•	Monitor monthly negotiated order value alongside average negotiated price and purchase-order volume to identify changes in procurement activity.
•	Compare prices within the same product categories or for identical items over time to distinguish genuine price increases from changes in purchasing mix.
•	Investigate the recurring March spending peaks with procurement or budget stakeholders before attributing them to a business cycle.
•	Treat January 2024 as a partial-period observation because it contains only two purchase orders; do not compare it directly with complete years or quarters.

# 7. Recommendations & Limitations
Recommendations
1.	Supplier Development: Initiate a quality improvement program with Delta_Logistics and Beta_Supplies to address their high defect rates.
2.	Contract Negotiation: Focus negotiations on Gamma_Co and Alpha_Inc, as they have the lowest total cost savings, to improve margin performance.
3.	Process Improvement: Investigate the root cause of Pending Orders (81) and Partially Delivered (73) orders to reduce working capital tied up in unfinished transactions.
4.	Data Governance: Implement validation rules in the source data-entry system to prevent logical flaws (e.g., a delivery date for a cancelled order) and eliminate invalid data points like the "del" category.
# Limitations
•	Savings Calculation: The calculated savings are based on the negotiated price versus the unit price. This represents cost avoidance or calculated savings, not realized savings (which would require baseline budget data). This distinction is critical to communicate.
•	Delivery Performance Metric: The Delivery_Performance is calculated for all orders, but an "On-Time" calculation only makes logical sense for orders that have actually been delivered. This was noted and the metric was interpreted with caution.
•	Data Granularity: The dataset does not include information on the reason for cancellations or defects, limiting the depth of root-cause analysis.


