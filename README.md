# Cafe-sales-analysis
This repository contains the excel analysis for the cafe sales data project. The primary goal was to process raw transaction data, handle various missing values using a combination of business logic and statistical proportionality, and derive meaningful insights into sales performance and product mix.

🧹 Data Cleaning Methodology

The cleaning process was specifically designed to impute missing values by leveraging known product pricing and purchase patterns to maintain data integrity.

1. Handling Missing Transaction Components
 
  - The core challenge was imputing missing values for Total Spent, Price, and Quantity using the known relationship: Total Spent = Price × Quantity.

  - Missing Total Spent (Item and Price Known): This was handled by directly calculating Total Spent using the formula.

  - Missing Price and Total Spent (Quantity Known): Three problematic rows (TXN_9646000, TXN_3611851, and TXN_7524977) only contained Quantity. Since the price was unknown and could not be reliably calculated without introducing bias,        these three rows were deleted from the dataset.

  - Missing Quantity and Total Spent (Item, Price Known): The missing Quantity was imputed as 1. This decision ensures that the Total Spent for that transaction is captured and prevents the overall revenue from being underestimated.
    

2. Imputing Missing Item Values
   
- Missing items were imputed based on known pricing for grouped items and their historical purchase percentages:

- Known Pricing:

  Sandwich and Smoothie items were priced at $4.

  Juice and Cake items were priced at $3.

- Imputation Strategy:

  Blank cells in the Item column were distributed proportionally between Juice and Cake based on their historical purchase percentages to minimize pattern bias:

  51% of blank items were imputed as Juice.

  49% of blank items were imputed as Cake.

  Did the same to the Sandwich and Smoothie.
  

3. Other Missing Value Handling
   
   Payment Method and Location: Missing values were filled with the category "Not defined". This treats the absence of data as a distinct and trackable category rather than ignoring the observation.
   

5. Date: Missing date values were imputed using the upper cell's value (Forward Fill). This assumes that the missing date belongs to the same business day as the preceding transaction.

Café Sales Analysis Dashboard:

•	**Financial Consistency**: Sales are highly consistent across months (CV of 3.6%), indicating a stable business model with low volatility.
The business model appears reliable from month to month, with little risk of extreme volatility.

![Coefficient Variation](images/coefficient)

-	**Product Profitability**: The highest revenue is driven by meal items (Salad, Sandwich), indicating the shop is successful as a lunch destination, not just a coffee shop.
Coffee sells the highest volume of units, confirming its importance as a staple item.

![Total Revenue Item](images/total-revenue-item)

- **Revenue Drivers (Day)**: The peak sales period is the late work week (Thursday and Friday). The business maintains very high and consistent revenue across almost every day of the week, with minimal drop-off, even on Wednesday (the   lowest day, 12447). The difference between the highest (Thu) and lowest (Wed) day is only about 4.4%.

 ![Daily Total Revenue](images/daily-total-revenue)

- **Preferred Payment Method**: Digital Wallet (2291 transactions) and Credit Card (2272 transactions) are almost equally popular and together account for the majority of transactions, surpassing Cash (2258).
	Insight: The customer base is heavily reliant on digital/card payments. Ensuring these systems are always operational is critical.

-	**Sales Channel**: Takeaway and In-store are an almost 50/50 split between dine-in and takeout. Any operational improvements should focus on optimizing the Takeaway process (order management, pick-up efficiency).
  ![Payment Method](images/payment-method) ![Sales by Location](images/sales-by-location)

  - **Peak Sales Months**: January and June are the highest sales months, with July showing a significant drop-off from the peak. It show a mid-year dip, possibly due to seasonality holiday or a specific event/promotion in Jan/Jun.

    ![Monthly Total Revenue](images/monthly-total-revenue)


**The core business is healthy, with high consistency and a strong base in meal-type items (Salad/Sandwich). The highest revenue occurs on Thu and Fri, but average performance is consistent, driven largely by Takeaway and digital payments.**

![Sales Dashboard](images/sales-dashboard)




  







