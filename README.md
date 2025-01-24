# Pizza Sales Analysis - Excel |MySql| Power BI Dashboard 

## Project Overview 🎯
This project aims to analyze key performance indicators (KPIs) and visualize various aspects of pizza sales data using Power BI. The analysis is based on the provided dataset [`pizza_sales.csv`](https://github.com/ankithkumar08/Pizza_sales-data-analysis-project/blob/main/pizza_sales.csv), and includes key insights such as revenue trends, sales by category, and the performance of different pizzas. The visualizations help us understand the performance of the pizza business in terms of sales, order trends, and popular products.

The dashboard answers the following business questions:
- What are the total sales and revenue generated from pizza orders?
- Which pizzas are performing well in terms of revenue and quantity sold?
- What are the sales trends by day and month?
- How do different pizza categories and sizes perform in terms of sales?

## KPI Requirements 🔎
The key performance indicators (KPIs) calculated for this analysis are:

1. **Total Revenue**: The sum of the total price of all pizza orders.
2. **Average Order Value**: The average amount spent per order.
3. **Total Pizzas Sold**: The sum of the quantities of all pizzas sold.
4. **Total Orders**: The total number of orders placed.
5. **Average Pizzas Per Order**: The average number of pizzas sold per order.

## Charts and Visualizations 📈
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

## SQL Queries 💡

### KPI Queries ✍🏻

1. **Total Revenue**:
   ```sql
   SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;
   
2. **Average Order Value**:
   ```sql
   SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales;
3. **Total Pizzas Sold**:
   ```sql
    SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales;
   
4. **Total Orders**:
    ```sql
      SELECT COUNT(DISTINCT order_id) AS Total_Orders 
      FROM pizza_sales;

5. **Average Pizzas Per Order**:
     ```sql
      SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
      CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2)) AS Avg_Pizzas_per_order
      FROM pizza_sales;


### Chart Queries 📊

1. **Daily Trend for Total Orders**:
   ```sql
    SELECT DAYNAME(order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
    FROM pizza_sales
    GROUP BY DAYNAME(order_date);
   
2. **Average Order Value**:
   ```sql
    SELECT MONTHNAME(order_date) AS Month_Name, COUNT(DISTINCT order_id) AS Total_Orders
    FROM pizza_sales
    GROUP BY MONTHNAME(order_date);


3. **Percentage of Sales by Pizza Category**:
   ```sql
    SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
    CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
    FROM pizza_sales
    GROUP BY pizza_category;
     
4. **Percentage of Sales by Pizza Size**:
   ```sql
       SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
       CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
       FROM pizza_sales
       GROUP BY pizza_size
       ORDER BY pizza_size;

5. **Pizzas Sold by Pizza Category Total**:
   ```sql
       SELECT pizza_category, SUM(quantity) AS Total_Quantity_Sold
       FROM  pizza_sales
       WHERE MONTH(order_date) = 2
       GROUP BY   pizza_category
       ORDER BY Total_Quantity_Sold DESC;
      
6. **Top 5 Pizzas by Revenue**:
   
   ```sql
    SELECT pizza_name, SUM(total_price) AS Total_Revenue
    FROM pizza_sales
    GROUP BY pizza_name
    ORDER BY Total_Revenue DESC
    LIMIT 5;
7. **Bottom 5 Pizzas by Revenue**:
   
    ```sql
   SELECT pizza_name, SUM(total_price) AS Total_Revenue
   FROM pizza_sales
   GROUP BY pizza_name
   ORDER BY Total_Revenue ASC
   LIMIT 5;
    
8. **Top 5 Pizzas by Quantity**: 
    ```sql
   SELECT pizza_name, SUM(quantity) AS Total_Pizza_Sold
   FROM pizza_sales
   GROUP BY pizza_name
   ORDER BY Total_Pizza_sold DESC  LIMIT 5;
9. **Bottom 5 Pizzas by Quantity:**
    ```sql
    SELECT pizza_name, SUM(quantity) AS Total_Pizza_sold
    FROM pizza_sales
    GROUP BY pizza_name
    ORDER BY Total_Pizza_sold ASC
    LIMIT 5;
10. **Top 5 Pizzas by Total Orders**:
     ```sql
    SELECT pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
    FROM pizza_sales
    GROUP BY pizza_name
    ORDER BY Total_Orders DESC
    LIMIT 5;
11. **Borrom 5 Pizzas by Total Orders**:
     ```sql
    SELECT pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
    FROM pizza_sales
    GROUP BY pizza_name
    ORDER BY Total_Orders ASC
    LIMIT 5;

## Dataset  🗂️ 🛒 

**The analysis is based on the dataset [pizza_sales.csv](https://github.com/ankithkumar08/Pizza_sales-data-analysis-project/blob/main/pizza_sales.csv), which contains the following columns**:

**Dataset Columns**
 <h2>📂 Dataset Columns</h2>
        <table>
            <thead>
                <tr>
                    <th>Column Name</th>
                    <th>Description</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td><code>pizza_id</code></td>
                    <td>Unique identifier for each pizza.</td>
                </tr>
                <tr>
                    <td><code>order_id</code></td>
                    <td>Unique identifier for each order.</td>
                </tr>
                <tr>
                    <td><code>pizza_name_id</code></td>
                    <td>Unique identifier linking to the pizza name.</td>
                </tr>
                <tr>
                    <td><code>quantity</code></td>
                    <td>Number of pizzas ordered.</td>
                </tr>
                <tr>
                    <td><code>order_date</code></td>
                    <td>Date when the order was placed.</td>
                </tr>
                <tr>
                    <td><code>order_time</code></td>
                    <td>Time when the order was placed.</td>
                </tr>
                <tr>
                    <td><code>unit_price</code></td>
                    <td>Price per unit of the pizza.</td>
                </tr>
                <tr>
                    <td><code>total_price</code></td>
                    <td>Total price of the order (calculated based on quantity and unit price).</td>
                </tr>
                <tr>
                    <td><code>pizza_size</code></td>
                    <td>Size of the pizza (e.g., Small, Medium, Large).</td>
                </tr>
                <tr>
                    <td><code>pizza_category</code></td>
                    <td>Category of the pizza (e.g., Vegetarian, Non-Vegetarian).</td>
                </tr>
                <tr>
                    <td><code>pizza_ingredients</code></td>
                    <td>Ingredients used in the pizza.</td>
                </tr>
                <tr>
                    <td><code>pizza_name</code></td>
                    <td>Name of the pizza.</td>
                </tr>
            </tbody>
        </table>

## Conclusion 💯🚀🎯
This project provides valuable insights into pizza sales data, enabling business stakeholders to make data-driven decisions. The Power BI dashboard allows users to interact with the data and explore different aspects of the sales performance, including revenue, popular pizzas, and order trends.

[Access the interactive Power BI Dashboard](https://github.com/ankithkumar08/Pizza_sales-data-analysis-project/blob/main/Project2.pbix)

## Connect with Me
Find out more about my journey and connect with me on [LinkedIn](www.linkedin.com/in/ankithkumar-chillapalli).

---

## Thank you for checking out my repository! Let’s code together! 💻

