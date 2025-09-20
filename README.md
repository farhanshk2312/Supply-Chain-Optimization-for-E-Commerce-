# E-Commerce Supply Chain Analytics Project

# Project Pipeline


Data Source(s): 

  (1) https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce             
    
  (2) https://www.kaggle.com/datasets/olistbr/marketing-funnel-olist
             

This is a Brazilian ecommerce public dataset of orders made at Olist Store. The dataset has information of 100k orders from 2016 to 2018 made at multiple marketplaces in Brazil. Its features allows viewing an order from multiple dimensions: from order status, price, payment and freight performance to customer location, product attributes and finally reviews written by customers. We also released a geolocation dataset that relates Brazilian zip codes to lat/lng coordinates.

This is real commercial data, it has been anonymised, and references to the companies and partners in the review text have been replaced with the names of Game of Thrones great houses.

It also includes a marketing funnel dataset from sellers that filled-in requests of contact to sell their products on Olist Store. The dataset has information of 8k Marketing Qualified Leads (MQLs) that requested contact between Jun. 1st 2017 and Jun 1st 2018. They were randomly sampled from the total of MQLs.

# Project Overview

The scope of the project is analyzing the e-commerce supply chain, including customer behavior, orders, warehouse operations, product demand, and promotions. The goal is to:

 1. Identify bottlenecks in delivery and inventory management.
  
 2. Optimize warehouse-to-customer routes.
  
 3. Forecast demand to reduce stockouts.
  
 4. Provide actionable dashboards for supply chain monitoring.

The project uses SQLite / SQL / Python / pandas, and is designed to be DBT-compatible for scalable ETL pipelines.


# Data Ingestion & ETL

Connect to database / raw CSV sources using Python or SQL.

Load raw tables (customers, orders, order_items, sellers, products, leads_closed).


1. Clean data:

  Handle missing values (e.g., missing zip codes or customer IDs).
  
  Ensure correct data types (timestamps, numeric columns).


2. Transform / Aggregate:

  Create daily_sales table: total units sold and revenue per product per warehouse per day.
  
  Create sales_with_promotions: flag products under promotion.
  
  Create demand_stats: calculate avg_daily_demand and std_daily_demand per product and warehouse.
  
  Load into warehouse / SQLite / DBT models.


# Exploratory Data Analysis (EDA)

1. Customer Analysis:

  Total customers, customer distribution by city/state.
  
  Missing customer info / data quality checks.


2.  Order Analysis:

  Orders per day, order status distribution.
  
  Delivery delays: calculate difference between order_estimated_delivery_date and order_delivered_customer_date.
  
  Identify top bottleneck warehouses or sellers.
      
    
3. Product Analysis:

  Most sold products by warehouse.
  
  Inventory levels vs. demand.
  
  Products under promotion and their sales lift.
  

# Supply Chain Insights

1. Delivery Delay Analysis:

  Compute average delay per warehouse.
  
  Identify warehouses with repeated delays for targeted process improvement.
  
  Warehouse-to-Customer Optimization:
  
  Map customer and warehouse zip codes.
  
  Suggest nearest warehouse fulfillment per product based on historical delivery times.

  
2. Demand Forecasting:

  Use demand_stats (mean ± std) to estimate daily demand ranges.
  
  Identify products at risk of stockouts.
  
  Optionally, integrate time-series forecasting (ARIMA, Prophet, or ML-based) for improved prediction.
  
  Promotion Impact Analysis:
  
  Compare units sold for products with promo_flag = 1 vs. non-promoted products.
  
  Compute revenue lift due to promotions.


# Future Enhancements

Integrate real-time inventory feeds to reduce stockouts.

Implement predictive delivery ETA models using ML.

Extend dashboards to include supplier lead times for full supply chain visibility.

Add dynamic pricing / promotion optimization based on demand forecasts.
