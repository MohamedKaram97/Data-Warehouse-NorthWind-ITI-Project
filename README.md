# DWH-NorthWind-Project 🎢🎡🎠

Welcome to our Data Warehouse (DWH) project! Below, you'll find a thrilling journey through the steps we've taken, complete with amusing icons to guide you along the way.

## 🚀 Project Milestones

### 1. Defining Business Processes
We've delved deep into the heart of our operations, uncovering the secrets that drive our organization's daily adventures.

### 2. Defining Granularity for the Analysis Scope
Establishing the level of detail in our analysis scope, ensuring that every twist and turn in our data is captured with precision.

### 3. Defining Dimensions for Analysis Context
Navigating through the dimensions of our data universe, discovering the realms where insights dwell.

### 4. Defining Facts and Measurements
We've measured the immeasurable, transforming raw data into golden nuggets of insight.

### 5. Data Warehouse Modeling (Defining the Schema)
Blueprints drawn, the architecture of our data kingdom laid bare for all to behold.

### 6. Physical Model Implementation
Bringing our data castle to life in the digital realm, one table at a time, with the magic of PostgreSQL and PGAdmin.

### 7. Data Warehouse Indexing
Equipping our data fortress with the finest indexing spells to ensure lightning-fast access to treasures untold.

### 8. Generating & Populating the Data
Breathing life into our data kingdom with the lifeblood of information, extracted, transformed, and loaded from the NorthWind database.

### 9. Writing SQL Queries to Gain Business Insights
Unleashing the power of SQL sorcery to extract wisdom from the depths of our data lake, illuminating the path to informed decisions.

## 📊 Tables Overview

### 1. Definition of Business Process 📦
- 🛒 The customer orders products from our company, embarking on a journey filled with excitement and anticipation.
- 🎉 Occasional promotions and discounts add a sprinkle of magic to the adventure.

### 2. Definition of Granularity 🔍
- The granularity of our fact table is as fine as a single product per order, capturing every detail of the quest.

### 3. Dimensions 🌐

#### DimCustomer 🧑‍🤝‍🧑
Comprehensive customer profiles await, filled with tales of their adventures and contact details.

#### DimDate 📅
A calendar of events, where every day holds a new story waiting to be told.

#### DimPromotion 🎁
Unlock the secrets of promotions past, present, and future, and their impact on our grand tale.

#### DimShipper 🚚
Navigate the seas of shipping with detailed shipper information at your fingertips.

#### DimSupplier 🏭
Journey to the realms of our suppliers, where treasures of inventory management await discovery.

#### DimProduct 📦
Discover the wonders of our product kingdom, from the humblest trinket to the grandest artifact.

#### DimProductPrice 💰
Uncover the secrets of pricing history, where every change tells a story of strategy and value.

#### DimTerritory 🗺️
Chart the lands of our sales territories, where regional performance meets geographical intrigue.

#### DimEmployee 👩‍💼
Meet the heroes behind the scenes, with detailed employee profiles and their ever-evolving roles.

#### DimEmpTerritory 🌍
Forge alliances between employees and territories, shaping the destiny of our sales empire.

#### DimPayMethodSaleChannel 💳
Navigate the channels of commerce, where payment methods and sales channels intertwine.

### 4. Fact Table 📊

#### Why Only One Fact Table? 🤔
- We've chosen to wield a single fact table, streamlining our quest for performance and efficiency.

#### What is the Grain? 🌾
- Each order fact is as intricate as every product within it, capturing the essence of each transaction.

#### What are the Foreign Keys (FKs)? 🔑
- Foreign keys unlock the doors to contextual insights, adding depth to our measurements.

#### What are the Measurements? 📏
- From shipping durations to profits earned, every metric paints a vivid picture of our adventures.

So, strap in and get ready for an exhilarating journey through the data realms, where insights await at every turn! 🎢✨


## Data Warehouse Modeling

In our Data Warehouse Modeling, we adopted the snowflake schema to establish relationships between the dimension tables.

So, strap in and get ready for an exhilarating journey through the data realms, where insights await at every turn! 🎢✨

![Model](https://github.com/Mostafa2096/DWH-NorthWind-Project/assets/106194954/91c0edbf-8e1d-4028-8a0e-b47431b2ce93)

## 📊 Business Questions & Power BI Dashboard

1. **Does order fulfillment speed (early vs. late deliveries) influence return rates among returned items?**
2. **How do Duels (Managers and their Employees (direct reports)) compare in terms of total profit generated and profit per day?**
3. **In each city we operate in, which product categories are the most profitable?**
4. **What are the preferred payment methods and sales channels?**
5. **In each city we operate in, what are the top 3 most frequently returned products?**
6. **Who are the top 5 customers, based on the total amount spent, in every city where we conduct business?**
7. **What Is The Impact Of Discounts On Profitability? (Profit With Vs. Without Discounts)**
8. **Which suppliers are the most valuable in terms of product variety?**
9. **Which suppliers are the most valuable in terms of overall profitability?**
10. **Which products are the most profitable during holidays based on quantity sold, total sales price, and total profit?**
11. **Which suppliers have the highest number of returned products?**

These questions guide our exploration of the data, aiming to uncover valuable insights that inform strategic decisions and drive business growth.

![Analysis Power BI Dashboard](https://github.com/Mostafa2096/DWH-NorthWind-Project/assets/106194954/1adc899c-7b8a-496a-8a3b-e0555e9cfc16)


## 📈 Indexes

1. **Bitmap Index on City Column in DimCustomer Table**
   - A bitmap index is chosen for the City column in the DimCustomer table due to its high cardinality nature. Cities often have numerous distinct values, making them suitable candidates for a bitmap index. This index type efficiently handles queries involving city-based filters or aggregations, such as counting customers by city, retrieving customers from specific cities, or analyzing customer distribution across different cities. By using a bitmap index, the database system can optimize query performance for city-related analytics and improve overall response times.

2. **Bitmap Index on Category Column in DimProduct Table**
   - Similar to the City column, the Category column in the DimProduct table is also expected to have high cardinality. Products are typically classified into various categories, resulting in a wide range of distinct category values. Utilizing a bitmap index on the Category column enables quick retrieval and analysis of products based on their categories. This index type is particularly beneficial for category-based reporting, analysis, and filtering operations. For example, it facilitates tasks such as analyzing sales performance by category, identifying top-selling categories, or comparing sales trends across different product categories.

3. **Hash Index on ProductName Column in DimProduct Table**
   - The ProductName column in the DimProduct table is often queried for exact matches, such as when users search for specific products by name. In such scenarios, a hash index on the ProductName column provides fast lookup performance for queries that require exact matching of product names. Hash indexes excel in handling equality searches, making them well-suited for this type of query pattern. By using a hash index, the database system can efficiently locate and retrieve products based on their names, enhancing user experience and query responsiveness.

4. **Default B-Tree Indexes on FactOrder Table Columns**
   - Several columns in the FactOrder table, including CustomerKey, EmployeeKey, PromotionKey, ShipperKey, and others, are indexed using default B-tree indexes. B-tree indexes are versatile and efficient for a wide range of queries, including range queries, equality searches, and sorting operations. These indexes enhance query performance for various order-related analytics, such as analyzing customer orders, evaluating employee performance, assessing promotional effectiveness, and optimizing shipping processes. By utilizing default B-tree indexes on these columns, the database system can handle diverse query requirements effectively and improve overall system performance.

5. **Default B-Tree Index on SupplierKey Column in DimProduct Table**
   - The SupplierKey column in the DimProduct table is indexed using a default B-tree index to optimize queries related to product suppliers. This index facilitates fast retrieval of products associated with specific suppliers, supplier performance analysis, supplier-related reporting, and supplier relationship management. By using a default B-tree index on the SupplierKey column, the database system can efficiently handle supplier-related queries and improve overall data retrieval performance.

6. **Default B-Tree Indexes on DimEmployee Table Columns**
   - Several columns in the DimEmployee table, including ManagerKey, and EffectiveToDateKey, are indexed using default B-tree indexes. These indexes support efficient employee-related queries, including hierarchical queries, tenure analysis, historical data retrieval, and workforce planning. By leveraging default B-tree indexes on these columns, the database system can optimize employee-related analytics, improve query performance, and facilitate data-driven decision-making in human resources management.

7. **Default B-Tree Indexes on DimProductPriceMini Table Columns**
   - The unitcost and unitprice columns in the DimProductPriceMini table are indexed using default B-tree indexes. These indexes aid in price analysis, cost comparisons, price trend analysis, and pricing strategy optimization for products over time. By using default B-tree indexes on these columns, the database system can efficiently handle price-related queries, support pricing decision-making processes, and improve overall data analysis capabilities.

### Performance Comparison:

![image](https://github.com/Mostafa2096/DWH-NorthWind-Project/assets/106194954/b16c550d-752d-4530-a7cf-65c733e3c690)


Note:
The details of the queries are in the queries pdf file.
