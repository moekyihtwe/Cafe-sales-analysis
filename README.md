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

  Did the samw to the Sandwich and Smoothie.
  

3. Other Missing Value Handling
   
   Payment Method and Location: Missing values were filled with the category "Not defined". This treats the absence of data as a distinct and trackable category rather than ignoring the observation.
   

5. Date: Missing date values were imputed using the upper cell's value (Forward Fill). This assumes that the missing date belongs to the same business day as the preceding transaction.

Dashboard Summary:

•	Financial Consistency: Sales are highly consistent across months (CV of 3.6%), indicating a stable business model with low volatility.
