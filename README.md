Online Retail Sales Analysis & RFM Customer Segmentation

An end-to-end Python analysis of more than 1 million transactions from a UK-based online gift and homeware retailer, covering data cleaning, sales trend analysis, statistical analysis, and RFM (Recency, Frequency, Monetary) customer segmentation with business recommendations.

Project Overview

The retailer sells gifts and home décor items, and most of its customers are wholesalers who buy in bulk. The dataset covers December 2009 to December 2011.

The project answers five business questions:

How do sales change from month to month?
Which countries and products bring in the most revenue?
At what time of day do customers place orders?
How much revenue comes from the top 20% of customers?
How can customers be grouped by buying behaviour (RFM), and what should the business do for each group?
Dataset
Source: Online Retail II – UCI Machine Learning Repository
File: online_retail_II.xlsx (two sheets: 2009–2010 and 2010–2011)
Size: about 1.07 million rows, 8 columns (Invoice, StockCode, Description, Quantity, InvoiceDate, Price, Customer ID, Country)

Note: The Excel file is about 45 MB, so it is stored in this repository using Git LFS. See How to Run below.

Tools & Libraries
Python
pandas – data cleaning and analysis
NumPy – summary statistics and log transforms
Matplotlib & Seaborn – visualisations
Jupyter Notebook
Data Cleaning
Combined both yearly sheets into one table and removed 34,335 duplicate rows
Filled missing product descriptions using the most common description for the same StockCode
Removed rows with no Customer ID (results are based on about 85% of sales)
Removed 18,390 cancelled-order rows (invoices starting with "C") and rows with zero or negative quantity or price
Checked outliers using summary statistics, log-scale boxplots, and the IQR method. Most outliers were genuine wholesale orders and were kept
Removed two huge orders (80,995 and 74,215 items) that were cancelled immediately, and 2,829 non-product rows (postage, bank charges, manual adjustments)
Created a Revenue column (Quantity × Price)

After cleaning: ~£16.8M in sales from 5,852 customers in 41 countries.

Analysis Performed
Monthly sales trend with the highest and lowest months highlighted
Top 10 countries by revenue, with and without the UK
UK vs overseas order value comparison
Top 10 products by revenue
Orders by hour of day
Pareto (80/20) analysis of customer revenue
Statistical analysis of R, F, and M: mean vs median, skewness, log transformation, and Spearman correlation
RFM segmentation using quintile scores (pd.qcut) and rule-based segments
Key Findings
Seasonality: Sales rise from September and peak in November (£1.16M in Nov 2010, £1.14M in Nov 2011), driven by pre-Christmas stocking. The lowest month was February 2011 (£0.44M).
Countries: The UK accounts for about 83% of revenue. The next biggest markets are Ireland, the Netherlands, Germany, and France.
Overseas orders: Overseas customers order less often but place bigger orders (median £419 vs £299 for UK customers).
Products: Top sellers are the Regency Cakestand 3 Tier and the White Hanging Heart T-Light Holder. Home décor and Christmas items dominate the top 10.
Order timing: Most orders arrive between 10:00 and 15:00, peaking at 12:00, consistent with business buyers.
80/20 rule: The top 20% of customers (1,170) generate 76.9% of revenue.
Skewed spending: The average customer spent £2,875, but the median customer spent only £856. Frequency and spending are strongly correlated (Spearman 0.86).
RFM Customer Segmentation
Segment	Customers	% of Customers	% of Revenue	Recommendation
Champions	1,476	25.2%	70.2%	Dedicated contact, volume discounts, early access to Christmas stock
Loyal	1,207	20.6%	14.4%	Volume discounts or bundles to grow order size
At Risk	828	14.1%	9.0%	Biggest win-back opportunity: personalised offers to top spenders first
New Customers	450	7.7%	1.5%	Welcome offer and discount on next order
Need Attention	382	6.5%	1.2%	Reminder or time-limited offer before they become Lost
Lost	1,509	25.8%	3.7%	Minimal spend: one low-cost win-back email at most

The top 50 Champions alone bring in 29% of all revenue, so the business depends heavily on a small group of buyers.

Business Recommendations
Prepare stock and promotions before autumn to capture the November peak
Grow sales in nearby European markets, where customers place larger orders
Send marketing emails in the late morning, just before the lunchtime order peak
Focus retention spending on Champions, and run win-back campaigns for At Risk customers, who spent £1.5M before going quiet
How to Run
Install Git LFS (needed to download the full Excel file):
bash
   git lfs install
Clone the repository:
bash
   git clone https://github.com/Sreelekha-j/Python-project-Online-Retail-Sales.git
   cd Python-project-Online-Retail-Sales
Install the required libraries:
bash
   pip install pandas numpy matplotlib seaborn openpyxl jupyter
Open the notebook and run all cells:
bash
   jupyter notebook

Keep the notebook and online_retail_II.xlsx in the same folder so the data loads correctly.

Repository Structure
Python-project-Online-Retail-Sales/
├── Python_project_Online Retail Sales.ipynb   # Main analysis notebook
├── online_retail_II.xlsx                      # Dataset (stored with Git LFS)
├── .gitattributes                             # Git LFS tracking settings
└── README.md
Author

Sreelekha J GitHub: Sreelekha-j
