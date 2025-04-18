# Tableau Instructions for StephenMart Data Exploration

This guide provides step-by-step instructions for using Tableau to explore the StephenMart dataset and answer the multiple-choice questions.

## Getting Started with the Data

### 1. Importing the Data
1. Open Tableau Desktop
2. Click on "Excel" under the Connect section
3. Navigate to and select the "StephenMart_Data.xlsx" file
4. You should see all five sheets: Sales_Transactions, Customer_Demographics, Product_Information, Store_Locations, and Promotions

### 2. Creating Data Relationships
For more complex questions, you'll need to relate these tables together:

1. Go to the Data Source tab
2. Drag each sheet into the canvas
3. Create the following relationships:
   - Connect Sales_Transactions to Product_Information using Product_ID
   - Connect Sales_Transactions to Customer_Demographics using Customer_ID
   - Connect Sales_Transactions to Store_Locations using Store_ID
   - Connect Promotions to Product_Information using Product_ID

## Answering Easy Questions (1-9)

### Question 1: Product Category Analysis
To find which product category has the highest revenue:

1. Create a new worksheet
2. Drag Product_Category from Product_Information to Rows
3. Drag Revenue from Sales_Transactions to Columns
4. Set the aggregation for Revenue to Sum
5. Sort the chart in descending order by Sum of Revenue

### Question 2: Discount Impact
To calculate the percentage of transactions with discounts:

1. Create a new worksheet
2. Drag Discount_Applied from Sales_Transactions to Rows
3. Drag Transaction_ID to Text on the Marks card, set to Count
4. Add a calculated field: [Count of Discount Y]/[Total Transactions]
   ```
   {FIXED : SUM(IF [Discount_Applied] = "Y" THEN 1 ELSE 0 END)} / {FIXED : COUNT([Transaction_ID])}
   ```
5. Format the calculated field as a percentage

### Question 3: Store Location Performance
To compare average transaction values by location type:

1. Create a new worksheet
2. Drag Location_Type from Store_Locations to Columns
3. Create a calculated field for transaction value:
   ```
   {FIXED [Transaction_ID] : SUM([Revenue])}
   ```
4. Drag this calculated field to Rows, set to Average
5. Add a reference line showing the overall average

### Question 4: Customer Demographics
To analyze customer age groups:

1. Create a new worksheet
2. Drag Age_Group from Customer_Demographics to Rows
3. Drag Customer_ID to Columns, set to Count (distinct)
4. Sort by Count of Customer_ID in descending order

### Question 5: Loyalty Program Distribution
To see loyalty tier distribution:

1. Create a new worksheet
2. Drag Loyalty_Status from Customer_Demographics to Columns
3. Drag Customer_ID to Rows, set to Count (distinct)
4. Add labels to see the exact counts

### Question 6: Product Price Analysis
To calculate average price per unit by category:

1. Create a new worksheet
2. Drag Product_Category from Product_Information to Rows
3. Create a calculated field for price per unit:
   ```
   SUM([Revenue]) / SUM([Quantity_Sold])
   ```
4. Drag this calculated field to Columns
5. Sort by the calculated field in descending order

### Question 7: Gender Distribution
To analyze gender distribution:

1. Create a new worksheet
2. Drag Gender from Customer_Demographics to Columns
3. Drag Customer_ID to Rows, set to Count (distinct)
4. Use a bar chart for clear comparison

### Question 8: Store Size Distribution
To find the most common store size:

1. Create a new worksheet
2. Drag Store_Size from Store_Locations to Rows
3. Drag Store_ID to Columns, set to Count (distinct)
4. Sort by Count of Store_ID in descending order

### Question 9: Promotion Types
To identify the most common promotion type:

1. Create a new worksheet
2. Drag Promotion_Type from Promotions to Rows
3. Drag Promotion_ID to Columns, set to Count
4. Sort by Count of Promotion_ID in descending order

## Answering Difficult Questions (10-12)

### Question 10: Multi-dimensional Performance Analysis
To compare average transaction values across multiple dimensions:

1. Create a new worksheet
2. Drag Loyalty_Status from Customer_Demographics to Columns
3. Drag Product_Category from Product_Information to Rows
4. Drag Location_Type from Store_Locations to Color on the Marks card
5. Create a calculated field for transaction value as we did earlier
6. Drag this calculated field to Text on the Marks card, set to Average
7. Create a highlight table to easily compare values
8. Use filters to narrow down to the combinations in the question

### Question 11: Discount Effectiveness Analysis
To analyze discount effectiveness across categories:

1. Create a new worksheet
2. First, calculate discount rate by category:
   ```
   {FIXED [Product_Category] : 
   SUM(IF [Discount_Applied] = "Y" THEN 1 ELSE 0 END) / 
   COUNT([Transaction_ID])}
   ```
3. Create a scatter plot with:
   - Discount rate on the X-axis
   - Average Revenue on the Y-axis
   - Product_Category on Color
4. Add a trend line to see the correlation
5. Create a second view showing before/after revenue comparison:
   - Drag Product_Category to Rows
   - Drag Discount_Applied to Columns
   - Drag Revenue to Text, set to Average
6. Compare the two views to determine the correct answer

### Question 12: Customer Behavior Pattern
This requires multiple analyses:

1. For age vs. spending:
   - Create a calculated field for transaction frequency by customer
   - Compare average transaction value and frequency across age groups

2. For gender and discounts:
   - Create a cross-tab with Gender and Discount_Applied
   - Calculate the percentage of discounted purchases by gender

3. For Bronze tier patterns:
   - Create a view with Loyalty_Status, Product_Category and Location_Type
   - Look for distinct patterns in the Bronze tier

4. For product variety by location:
   - Create a calculated field for distinct products per transaction
   - Compare this metric across location types

