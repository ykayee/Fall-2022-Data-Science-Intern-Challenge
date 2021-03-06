# Fall-2022-Data-Science-Intern-Challenge

## **Question 1:**
**a. Think about what could be going wrong with our calculation. Think about a better way to evaluate this data.**   
- The attached code includes the thinking process, data visualization, analysis and the methods being used to solve this question. 
- Even though the sneakers is selling in a affordable price, the AOV is relatively high. The reason why it happens is due to the outliers in the dataset. I created a new column “cost_per_item” to calculate the selling price for one pair of sneakers. After analysing the data, it is not a normal distribution. I observed that the orders from user_id 607 and shop_id 78 are the outliers.   

- User_id 607 made some bulk purchases with 2,000 items with total amount of $704,000 per orders. It heavily increased the AOV while majority of the customers are purchasing a few numbers of items per orders.   

- Shop_id 78 is selling sneakers with $25725.0 for each item, which violates the affordable item stated on the question. It is extremely higher than the price per item compared to the rest of the 99 shops. It also affects the accuracy of AOV while the other shops are selling their sneakers in an affordable price.   

- I used z-socre to evaluate the data. The z-score in cost_per_item and order_amount with larger than 3 are considered as outliers. I dropped those orders out of the data.  

- The AOV without outliers is decreased from 3145.13 to 302.58, which looks much more reasonable for these shops selling affordable sneakers.  

**b. What metric would you report for this dataset?** 

- The matric of median is better than the mean for reporting the AOV. Using median could reduce the effect of the extremely large values(outliers) on calculating the AOV. The median order value of the dataset with and without outliers are the same. In this case, extreme outliers did not effect the median.   

**c. What is its value?**

	284.0

## **Question 2:**
**a. How many orders were shipped by Speedy Express in total?**  
```
54.0
```
```
SELECT COUNT(o.OrderID) 
FROM Orders o JOIN Shippers s
ON o.ShipperID = s.ShipperID
WHERE s.ShipperName ='Speedy Express'
```

**b. What is the last name of the employee with the most orders?**  
```
Peacock
```
```
SELECT LastName
FROM Orders o JOIN Employees e
ON o.EmployeeID = e.EmployeeID
GROUP BY o.EmployeeID
ORDER BY COUNT(o.OrderID) DESC
LIMIT 1
```

**c. What product was ordered the most by customers in Germany?**
```
Boston Crab Meat
```
```
With Germany AS(
SELECT Orders.OrderID FROM Customers JOIN Orders
ON Customers.CustomerID = Orders.CustomerID
WHERE Country = 'Germany')

SELECT Products.ProductName
From Germany JOIN OrderDetails
ON Germany.OrderID = OrderDetails.OrderID
JOIN Products
ON OrderDetails.ProductID=Products.ProductID
GROUP BY Products.ProductID
ORDER BY SUM(Quantity) DESC
Limit 1
```
