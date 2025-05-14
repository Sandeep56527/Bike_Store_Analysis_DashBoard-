# Bike_Store_Analysis_DashBoard-
Table of Contents
Project Overview
Data Sources
Tools Used
Exploratory Data Analysis
Data Preparation
Report Creation
Results
Project Overview
This data analysis project aims to provide insights into the sales performance of a Bike Store company over the past years. By analyzing various aspects of the sales data, we seek to identify trends, make data-driven recommendations, and gain a deeper understanding of the company's performance.

Data Sources
Sales Data: The primary dataset used for this analysis is the "SalesData.csv" file, containing detailed information about each sale made by the company. This "SalesData.csv" is derived from joining different tables such as "production.brands", "production.categories", "production.products", "production.stocks", "sales.customers", "sales.order_items", "sales.orders", "sales.staffs", "sales.stores".

Tools Used
Microsoft Excel (for Data Cleaning)
Download Here for MS Excel
Microsoft SQL Server (for Data Analysis)
Download Here for MS SQL Server
Tableau (for Creating Reports)
Download Here for Tableau Desktop
Exploratory Data Analysis
EDA involved exploring the sales data to answer key questions, such as:

revenue generated year by year.
revenue generated per store.
Who are our Top Customers?
Data Preparation
I joined multiple tables like ( "production.brands", "production.categories", "production.products", "production.stocks", "sales.customers", "sales.order_items", "sales.orders", "sales.staffs", "sales.stores" ) to retrive SalesData by using inner join because I only need matching records.

SQL Query Used to Join these tables
SELECT
	o.order_id,
	CONCAT(c.first_name,' ',c.last_name) AS 'customer_full_name',
	c.city,
	c.state,
	o.order_date,
	SUM(oi.quantity)AS 'total_units',
	SUM(oi.quantity * oi.list_price) AS 'revenue',
	p.product_name,
	ca.category_name,
	s.store_name,
	CONCAT(st.first_name,' ',st.last_name) AS Store_Representative,
	b.brand_name
FROM BikeStores.sales.customers c join BikeStores.sales.orders o
ON c.customer_id = o.customer_id join BikeStores.sales.order_items oi
ON o.order_id = oi.order_id join BikeStores.production.products p
ON oi.product_id = p.product_id join BikeStores.production.categories ca
ON p.category_id = ca.category_id join BikeStores.sales.stores s
ON o.store_id = s.store_id join BikeStores.sales.staffs st
ON s.store_id = st.store_id join BikeStores.production.brands b
ON p.brand_id = b.brand_id
GROUP BY
	o.order_id,
	CONCAT(c.first_name,' ',c.last_name),
	c.city,
	c.state,
	o.order_date,
	p.product_name,
	ca.category_name,
	s.store_name,
	CONCAT(st.first_name,' ',st.last_name),
	b.brand_name;
Report Creation
Created final Dashboard by using Tableau image
![Dashboard Preview](https://github.com/Sandeep56527/Bike_Store_Analysis_DashBoard-/blob/56c59e214481fd0bba631463f7736e6b69cf588b/Dashboard%201.png)

to access the dashboard directly please Click Here
Results
The analysis results are summarized as follows:

The company has recorded the highest revenue in the year 2017.
Baldwin Bikes store has made a major contribution to it.
Texas is the highest revenue-generating state.
Trek is the overall most-selling brand.
Mountain Bikes are much sold followed by Road Bikes and more...
Pamelia Newman is our overall top customer followed by Abby Gamble and more...
