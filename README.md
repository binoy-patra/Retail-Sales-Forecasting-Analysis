# Retail-Sales-Forecasting-Analysis-With Walmart 

## Table of Contents
- [Introduction](#introduction)
- [Purposes Of The Project](#purposes-of-the-project)
- [Dataset Overview](#dataset_overview)
- [Analysis Overview](#analysis-overview)
- [Approach Used](#approach-used)
- [Business Questions To Answer](#business-questions-to-answer)
- [Overall Insights](#overall-insights)
- [Tools Used](#tools-used)
- [Recommendations](#recommendations)
- [File Descriptions](#file-descriptions)
- [Future Improvements](#future-improvements)
- [Contributing](#contributing)
- [Contact Me](#contact-me)

  
## Introduction:

In the contemporary retail landscape, data-driven decision-making is pivotal for maintaining competitive advantage. This analysis of Walmart's sales data employs Structured Query Language (SQL) to unearth key insights that can inform strategic decisions. By dissecting various dimensions such as customer types, product lines, and sales performance across different times and days, this report aims to provide a comprehensive understanding of consumer behavior and sales dynamics.

## Purposes Of The Project

The major aim of thie project is to gain insight into the sales data of Walmart to understand the different factors that affect sales of the different branches.

## Dataset Overview

The dataset was obtained from the [Kaggle Walmart Sales Forecasting Competition](https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting).     
This dataset contains sales transactions from a three different branches of Walmart, respectively located in Mandalay, Yangon and Naypyitaw.    
The data contains 17 columns and 1000 rows:

| Column                  | Description                             | Data Type      |
| :---------------------- | :-------------------------------------- | :------------- |
| invoice_id              | Invoice of the sales made               | VARCHAR(30)    |
| branch                  | Branch at which sales were made         | VARCHAR(5)     |
| city                    | The location of the branch              | VARCHAR(30)    |
| customer_type           | The type of the customer                | VARCHAR(30)    |
| gender                  | Gender of the customer making purchase  | VARCHAR(10)    |
| product_line            | Product line of the product solf        | VARCHAR(100)   |
| unit_price              | The price of each product               | DECIMAL(10, 2) |
| quantity                | The amount of the product sold          | INT            |
| VAT                 | The amount of tax on the purchase       | FLOAT(6, 4)    |
| total                   | The total cost of the purchase          | DECIMAL(10, 2) |
| date                    | The date on which the purchase was made | DATE           |
| time                    | The time at which the purchase was made | TIMESTAMP      |
| payment_method                 | The total amount paid                   | DECIMAL(10, 2) |
| cogs                    | Cost Of Goods sold                      | DECIMAL(10, 2) |
| gross_margin_percentage | Gross margin percentage                 | FLOAT(11, 9)   |
| gross_income            | Gross Income                            | DECIMAL(10, 2) |
| rating                  | Rating                                  | FLOAT(2, 1)    |

### Analysis Overview

1. Product Analysis
   
> Conduct analysis on the data to understand the different product lines, the products lines performing best and the product lines that need to be improved.

2. Sales Analysis

> This analysis aims to answer the question of the sales trends of product. The result of this can help use measure the effectiveness of each sales strategy the business applies and what modificatoins are needed to gain more sales.

3. Customer Analysis

> This analysis aims to uncover the different customers segments, purchase trends and the profitability of each customer segment.

## Approach Used

1. **Data Wrangling:** This is the first step where inspection of data is done to make sure **NULL** values and missing values are detected and data replacement methods are used to replace, missing or **NULL** values.

> 1. Build a database
> 2. Create table and insert the data.
> 3. Select columns with null values in them. There are no null values in our database as in creating the tables, we set **NOT NULL** for each field, hence null values are filtered out.

2. **Feature Engineering:** This will help use generate some new columns from existing ones.

> 1. Add a new column named `time_of_day` to give insight of sales in the Morning, Afternoon and Evening. This will help answer the question on which part of the day most sales are made.

> 2. Add a new column named `day_name` that contains the extracted days of the week on which the given transaction took place (Mon, Tue, Wed, Thur, Fri). This will help answer the question on which week of the day each branch is busiest.

> 3. Add a new column named `month_name` that contains the extracted months of the year on which the given transaction took place (Jan, Feb, Mar). Help determine which month of the year has the most sales and profit.

2. **Exploratory Data Analysis (EDA):** Exploratory data analysis is done to answer the listed questions and aims of this project.


## Business Questions To Answer

### Generic Question

1. How many unique cities does the data have?
2. In which city is each branch?

### Product

1. How many unique product lines does the data have?
2. What is the most common payment method?
3. What is the most selling product line?
4. What is the total revenue by month?
5. What month had the largest COGS?
6. What product line had the largest revenue?
5. What is the city with the largest revenue?
6. What product line had the largest VAT?
7. Fetch each product line and add a column to those product line showing "Good", "Bad". Good if its greater than average sales
8. Which branch sold more products than average product sold?
9. What is the most common product line by gender?
12. What is the average rating of each product line?

### Sales

1. Number of sales made in each time of the day per weekday
2. Which of the customer types brings the most revenue?
3. Which city has the largest tax percent/ VAT (**Value Added Tax**)?
4. Which customer type pays the most in VAT?

### Customer

1. How many unique customer types does the data have?
2. How many unique payment methods does the data have?
3. What is the most common customer type?
4. Which customer type buys the most?
5. What is the gender of most of the customers?
6. What is the gender distribution per branch?
7. Which time of the day do customers give most ratings?
8. Which time of the day do customers give most ratings per branch?
9. Which day fo the week has the best avg ratings?
10. Which day of the week has the best average ratings per branch?


## Revenue And Profit Calculations

$ COGS = unitsPrice * quantity $

$ VAT = 5\% * COGS $

$VAT$ is added to the $COGS$ and this is what is billed to the customer.

$ total(gross_sales) = VAT + COGS $

$ grossProfit(grossIncome) = total(gross_sales) - COGS $

**Gross Margin** is gross profit expressed in percentage of the total(gross profit/revenue)

$ \text{Gross Margin} = \frac{\text{gross income}}{\text{total revenue}} $

<u>**Example with the first row in our DB:**</u>

**Data given:**

- $ \text{Unite Price} = 45.79 $
- $ \text{Quantity} = 7 $

$ COGS = 45.79 * 7 = 320.53 $

$ \text{VAT} = 5\% * COGS\\= 5\%  320.53 = 16.0265 $

$ total = VAT + COGS\\= 16.0265 + 320.53 = $336.5565$

$ \text{Gross Margin Percentage} = \frac{\text{gross income}}{\text{total revenue}}\\=\frac{16.0265}{336.5565} = 0.047619\\\approx 4.7619\% $


### Overall Insights

The analysis of Walmart's sales data offers several key insights:

1. **Geographic and Branch Insights:**
   - There are three cities covered: Yangon, Naypyitaw, and Mandalay.
   - Branch A is in Yangon, Branch B is in Mandalay, and Branch C is in Naypyitaw.
   - Naypyitaw (Branch C) generates the highest revenue.

2. **Revenue and Costs:**
   - The total revenue across all branches is $320,886.39.
   - The total Cost of Goods Sold (CoG) is $305,606.09.

3. **Product Analysis:**
   - There are six unique product lines, with "Electronic accessories" being the top seller by quantity.
   - "Food and beverages" is the product line with the highest revenue.
   - Cash is the most common payment method.
   - January recorded the highest revenue and CoG among the months analyzed.

4. **Sales Analysis:**
   - The evening time sees the highest sales, followed by the afternoon and morning.
   - Members contribute slightly more to revenue than Normal customers.
   - Naypyitaw has the highest average tax percentage.

5. **Customer Insights:**
   - The customer base is evenly split between Normal and Member types.
   - Gender distribution is almost equal, with slightly more male customers.
   - Afternoon is the time of day when customers give the highest ratings, with Monday being the day with the best average ratings.

6. **Product Line Performance:**
   - The top three product lines by revenue are "Food and beverages," "Fashion accessories," and "Sports and travel."
   - "Health and beauty" shows the highest VAT, followed by "Sports and travel."

These insights can help Walmart optimize its operations, tailor marketing strategies, and improve customer satisfaction and sales efficiency across different branches and product lines.


### Tools Used :
- **MySQL** 
- **Canava**

### Recommendations

Based on the analysis of Walmart's sales data, the following recommendations are proposed to optimize operations, enhance customer satisfaction, and boost sales:

1. **Optimize Inventory for High-Performing Product Lines:**
   - Electronic accessories and Food and beverages are the top-performing product lines. Ensure these items are always well-stocked to meet demand.
   - Focus marketing and promotional efforts on these categories to capitalize on their popularity.

2. **Enhance Marketing for Underperforming Categories:**
   - Fashion accessories and Health and beauty have lower sales compared to other categories. Develop targeted marketing campaigns to boost sales in these areas.
   - Consider customer feedback and trends to adjust the product mix within these categories.

3. **Leverage High Revenue Periods:**
   - January has been identified as the month with the highest revenue. Plan special promotions and sales events during this period to maximize sales.
   - Analyze reasons behind the January peak and apply similar strategies to other months.

4. **Tailor Customer Experience:**
   - Evening is the peak time for sales. Ensure sufficient staffing and inventory during these hours to provide excellent customer service.
   - Enhance the shopping experience during evenings with in-store events, discounts, or special offers.

5. **Focus on High Revenue Branches:**
   - Naypyitaw (Branch C) generates the highest revenue. Consider using successful strategies from this branch as a model for others.
   - Conduct a detailed analysis of customer preferences and behaviors in Naypyitaw to replicate success in other cities.

6. **Improve Payment Method Options:**
   - Cash is the most common payment method, but a significant number of customers use E-wallets and credit cards. Ensure all payment systems are quick, secure, and user-friendly to enhance customer convenience.

7. **Enhance Customer Loyalty Programs:**
   - Members contribute slightly more to revenue than normal customers. Enhance loyalty programs to encourage more customers to become members.
   - Offer exclusive discounts, early access to sales, and special promotions to members to increase retention and attract new sign-ups.

8. **Utilize Customer Feedback for Improvements:**
   - Afternoon has the highest customer ratings, followed by the morning and evening. Investigate the reasons for higher satisfaction during these periods and apply similar strategies to other times.
   - Regularly collect and analyze customer feedback to identify areas for improvement and implement changes promptly.

9. **Capitalize on High-Rating Days:**
   - Monday has the best average ratings. Consider extending successful Monday strategies to other days to improve overall customer satisfaction.

10. **Monitor and Adjust VAT Strategies:**
    - Naypyitaw has the highest average tax percentage. Monitor the impact of VAT on sales and adjust pricing strategies if necessary to maintain competitiveness without sacrificing profitability.

By implementing these recommendations, Walmart can optimize its operations, improve customer satisfaction, and drive higher sales across its branches.


## File Descriptions

- **SQL_Queries.sql**: MySQL script containing codes.
- **Dataset**: Dataset folder containing the walmart sales data, datamodel and walmart logo
- **README.md**: Documentation file providing an overview of the project.

## Future Improvements

- Expand analysis to include more advanced machine learning models for predictive analysis.
## Contributing

Contributions to improve the analysis scripts, add new features, or fix issues are welcome. Please fork the repository, make your changes, and submit a pull request.

## Contact Me

- **LinkedIn**: [Binoy Patra](https://www.linkedin.com/in/binoy-patra-b9277b1b2?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=android_app)
- **GitHub**: [Binoy Patra](https://github.com/binoy-patra)
- **Gmail**: binoypatra20@gmail.com
