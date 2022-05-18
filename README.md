# Fall-2022-Data-Science-Intern-Challenge

Question 1:  
Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 
Even though the sneakers is selling in a affordable price, the AOV is relatively high. The reason why it happens is due to the outliers in the dataset. I created a new column “cost_per_item” to calculate the selling price for one pair of sneakers. After analysing the data, it is not a normal distribution. I observed that the orders from user_id 607 and shop_id 78 are the outliers.   

User_id 607 made some bulk purchases with 2,000 items with total amount of $704,000 per orders. It heavily increased the AOV while majority of the customers are purchasing a few numbers of items per orders.   

Shop_id 78 is selling sneakers with $25725.0 for each item, which violates the affordable item stated on the question. It is extremely higher than the price per item compared to the rest of the 99 shops. It also affects the accuracy of AOV while the other shops are selling their sneakers in an affordable price.   

I used z-socre to evaluate the data. The z-score in cost_per_item and order_amount with larger than 3 are considered as outliers. I dropped those orders out of the data.  

The AOV without outliers is decreased from 3145.13 to 302.58, which looks much more reasonable for these shops selling affordable sneakers.  
