# Pizza Sales Analysis - Excel |MySql| Power BI Dashboard  

## Project Overview
This project aims to analyze key performance indicators (KPIs) and visualize various aspects of pizza sales data using Power BI. The analysis is based on the provided dataset `pizza_sales.csv`, and includes key insights such as revenue trends, sales by category, and the performance of different pizzas. The visualizations help us understand the performance of the pizza business in terms of sales, order trends, and popular products.

The dashboard answers the following business questions:
- What are the total sales and revenue generated from pizza orders?
- Which pizzas are performing well in terms of revenue and quantity sold?
- What are the sales trends by day and month?
- How do different pizza categories and sizes perform in terms of sales?

## KPI Requirements
The key performance indicators (KPIs) calculated for this analysis are:

1. **Total Revenue**: The sum of the total price of all pizza orders.
2. **Average Order Value**: The average amount spent per order.
3. **Total Pizzas Sold**: The sum of the quantities of all pizzas sold.
4. **Total Orders**: The total number of orders placed.
5. **Average Pizzas Per Order**: The average number of pizzas sold per order.

## Charts and Visualizations
1. **Daily Trend for Total Orders**
   - **Description**: A bar chart displaying the daily trend of total orders.
   - **Purpose**: To identify any patterns or fluctuations in order volumes on a daily basis.

2. **Monthly Trend for Total Orders**
   - **Description**: A line chart illustrating the monthly trend of total orders.
   - **Purpose**: To identify peak months or periods of high order activity.

3. **Percentage of Sales by Pizza Category**
   - **Description**: A pie chart showing the distribution of sales across different pizza categories.
   - **Purpose**: To understand customer preferences for various pizza categories and their contribution to overall sales.

4. **Percentage of Sales by Pizza Size**
   - **Description**: A pie chart representing the percentage of sales attributed to different pizza sizes.
   - **Purpose**: To understand customer preferences for pizza sizes and their impact on sales.

5. **Total Pizzas Sold by Pizza Category**
   - **Description**: A funnel chart presenting the total number of pizzas sold for each pizza category.
   - **Purpose**: To compare the sales performance of different pizza categories.

6. **Top 5 Best Sellers by Revenue, Quantity, and Orders**
   - **Description**: A bar chart highlighting the top 5 best-selling pizzas based on Revenue, Total Quantity, and Total Orders.
   - **Purpose**: To identify the most popular pizza options.

7. **Bottom 5 Best Sellers by Revenue, Quantity, and Orders**
   - **Description**: A bar chart showcasing the bottom 5 worst-selling pizzas based on Revenue, Total Quantity, and Total Orders.
   - **Purpose**: To identify underperforming or less popular pizza options.

## SQL Queries

### KPI Queries

1. **Total Revenue**:
   ```sql
   SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;
   
2. **Average Order Value**:
    ```sql
   SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales;
3 **Total Pizzas Sold**:
```sql
 SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales;

4 **Total Orders**: 
