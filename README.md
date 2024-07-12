

# Coffee Shop Sales Dashboard

## About Project

This dashboard helps us know how we understand, manage, and grow coffee business for first half of 2023. It helps the business to know the customer prefences on the products.
Also this helps to understand the peak sales period of the day, & thus the business at all locations can reevaluate the opening and closing hour. This also shows the location which has the highest revenue among others.
By providing real-time insights into sales performance, customer preferences and market trends, the dashboard empowers us to optimize operations, enhance customer experiences, and drive revenue growth.



### Steps taken:

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : Creating fact and dimension tables by referencing the original table and removing the unwanted columns to create the dimension tables and fact table. 
- Step 5 : Removing all duplicates from the dimension tables.
- Step 6 : Adding "Hour" column by extracting it from thr "transaction_time" column.
- Step 7 : Adding "Total Sales" column by multiplying "transaction_qty" and "unit_price" columns together.

- Below are the preview of the fact and dimension tables; 

![fact 1](https://github.com/user-attachments/assets/abb3151d-bcaa-4733-9555-407659a540f1)

![fact 2](https://github.com/user-attachments/assets/584d6618-4bfe-41a2-ac43-33084150027e)

![product data](https://github.com/user-attachments/assets/6ef2f695-d170-4c7b-95f7-8a27567091d4)

![store data](https://github.com/user-attachments/assets/d50b64d5-39e1-4108-8871-1eb02816201a)

- Step 8 : Creating a Date table.
- Step 9 : After closing and applying the queries from the query editor. Some new measures were created using DAX expressions;

	1. % of Sales = DIVIDE([Total Sales], CALCULATE([Total Sales], ALLSELECTED('Product')))

	2. AVG Order Sales = AVERAGE(Transactions_fact[Total Sales])

	3. AVG Unit Price = AVERAGE(Transactions_fact[unit_price])

	4. Max AVG Order Sales (Hour) = MAXX(ALLSELECTED(Transactions_fact[Hour]),[AVG Order Sales])

	5. Max AOS Marker = SWITCH(TRUE(), [AVG Order Sales] = [Max AVG Order Sales (Hour)], [AVG Order Sales], BLANK())

	6. Max AOS Marker Label = "Max AVG Order Sales: " & FORMAT([Max AOS Marker], "$###,##0.00")

	7. Number of Stores = DISTINCTCOUNT(Store[store_id])

	8. Total Products = DISTINCTCOUNT('Product'[product_id])

	9. Total Sales = SUM(Transactions_fact[Total Sales])

	10. Total Transactions = DISTINCTCOUNT(Transactions_fact[transaction_id])

### Data Analysis:
- Analyzed sales data to identify Product performance, Peak sales periods, and Store performance.
- Used charts, cards, slicers and bookmarks to organize and summarize the data effectively.

### Data Visualization:
- Created clear and informative charts and graphs to visualize key insights.
- Developed dashboards in Power Bi to display data trends and patterns in an easily understandable format.

### Key Insights:
1. Used card visuals to represent the following;
- Total Sales
- Average Order Sales
- Average Unit Price
- Total Transactions
- Number of Products
- Number of Stores
2. Used slicers to filter for store and month.

- Bookmark was used to show the below inights with the above inights on each page of the views;

1. Product Insights:
- Total sales by product category, using tooltip to also show the % of sales for each product.
- Total sales by product detail.
- Top 10 product by total sales.
![product](https://github.com/user-attachments/assets/eef24730-d806-4d2b-95be-2fec0ffa3bca)

2. Time Visuals:
- Analyzed peak sales hours and day of the week with the most sales.
- Determing the hour with the maximum average order sales.
- % of total sales by time of the day

![time visual](https://github.com/user-attachments/assets/735060da-a317-43c1-936d-894b861bc469)

3. Stores Insights:
- Visualizing how stores performs in the each month of the 2023 first half.
- Total transaction by store location.

![stores](https://github.com/user-attachments/assets/4b43bff5-8af7-424e-90b2-fa9129a915e4)


Following inferences can be draw from the dashboard;

1. So far in 2023, Total Sales is ﻿$698,812﻿ and Total Transactions is ﻿149,116﻿. 
Coffee has the highest sales of $269,952.45 and 39% of the Total sales among all Product Category. 
Barista Espresso is the best seller among all Product Type with a Total Sales of ﻿$91,406﻿. 
Also Sustainably Grown Organic LG is the strongest seller in terms of Revenue. 

2. Sales start to peak at 7 AM. The most popular period when we generate more revenue is at 10 AM and the least period when we generate revenue is at 8 PM. 
Monday is our highest generating revenue while Saturday is the lowest generating revenue day of the week.
What we are noticing, is that our sales take off more in the Morning than in the other times of the day.

3. Hell's Kitchen sold the highest number of transactions sold 50,735 (34.02% of total transactions) and total sales of $236,511.
It is also shown that more revenue is generated in the Month of June with total sales of $166,486 and February generated the least revenue of $76,145.
While Lower Manhattan has the least number of transactions sold 47,782 and total sales of $230,057.

### Conclusion;
The insights derived from this analysis enabled stakeholders to make informed decisions that positively impacted the coffee shop's operations:

- Inventory Management: Optimized stock levels based on product demand and ensuring popular items were always available especially in the morning.

- Marketing Strategies: Enhanced marketing efforts by targeting promotions during peak sales periods and highlighting customer favorites.

- Revenue Growth: Implemented strategies that boosted overall revenue, such as introducing high-performing products and optimizing pricing.

This project showcases the power of data analytics in driving business success.


