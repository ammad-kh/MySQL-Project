# MySQL-Project
Telco Customers Churn Analysis Project
1. Project Overview
This project involves analyzing customer churn for a telecommunications company using the Telco Customers Churn dataset. The primary objective is to gain insights into customer behavior, satisfaction, and churn tendencies by transforming and analyzing the data. The analysis is performed by transitioning from an OLTP (Online Transaction Processing) system to an OLAP (Online Analytical Processing) system, enabling better visualization and understanding of key performance indicators (KPIs).
________________________________________
2. Dataset Description
The Telco Customers Churn dataset contains information about customers, their services, payments, locations, and churn status. Key columns include:
●	Customer Details: Gender, age, marital status, dependents, senior citizen status.
●	Service Details: Internet service, phone service, and offers.
●	Payment Details: Contract type, payment method, and total charges.
●	Churn Metrics: Churn label, churn score, customer lifetime value (CLTV), satisfaction score.
________________________________________
3. OLTP to OLAP Conversion
The dataset initially exists in an OLTP structure, with normalized tables optimized for transactions. To perform analytical queries efficiently, it was converted into an OLAP schema, following these steps:
3.1. Data Extraction
Data was extracted from multiple tables, including:
●	Customer_Info
●	Payment_Info
●	Service_Options
●	Location_Data
●	Status_Analysis
3.2. Data Transformation
Each table was denormalized and restructured into a star schema with one fact table and multiple dimension tables.
3.3. Data Loading
The transformed tables were loaded into an OLAP structure for analysis. The database schema, named telco_customers_olap, consists of the following tables:
●	Fact Table: churn_fact
●	Dimension Tables: customer_dim, payment_dim, service_dim, location_dim
________________________________________
4. Star Schema Design
The star schema organizes the data into a central fact table and surrounding dimension tables:
4.1. Fact Table
churn_fact contains numerical and measurable data:
●	customer_id (foreign key)
●	churn_score
●	churn_label
●	satisfaction_score
●	cltv
●	total_revenue
4.2. Dimension Tables
●	customer_dim

○	customer_id (primary key)
○	gender, age, marital_status, dependents, senior_citizen
●	payment_dim

○	customer_id (primary key)
○	contract, payment_method, total_charges
●	service_dim

○	customer_id (primary key)
○	internet_service, phone_service, offer
●	location_dim

○	customer_id (primary key)
○	country, state, city, zip_code, total_population
________________________________________
5. Data Warehousing Process
5.1. Schema Creation
The OLAP schema was created in MySQL using SQL queries to define the structure of the fact and dimension tables.
5.2. Data Population
Data from OLTP tables was inserted into the OLAP tables using SQL INSERT INTO SELECT statements. Primary and foreign keys were established to ensure referential integrity.
5.3. Queries for Analysis
SQL queries were written to calculate KPIs and prepare data for visualization.
________________________________________
6. Key Performance Indicators (KPIs)
KPI 1: Churn Rate
●	Definition: Percentage of customers who have churned.
●	Visualization: Card.
DAX Formula:
 Churn Rate (%) = DIVIDE([Churned Customers], [Total Customers]) * 100

KPI 2: Average Monthly Revenue
●	Definition: Average total revenue per customer.
●	Visualization: Card.
KPI 3: Customer Satisfaction by Internet Service
●	Definition: Average satisfaction score segmented by internet service type.
●	Visualization: Bar chart with internet service on the X-axis and average satisfaction score on the Y-axis.
KPI 4: Payment Method Preferences
●	Definition: Distribution of customers by payment method.
●	Visualization: Pie chart with payment method as the legend and count of customers as values.
KPI 5: Contract Type vs. Churn Rate
●	Definition: Churn rate segmented by contract type.
●	Visualization: Clustered bar chart with contract type on the X-axis and count of churned customers on the Y-axis.
KPI 6: Dependents' Impact on Churn
●	Definition: Churn rate comparison between customers with and without dependents.
●	Visualization: Clustered bar chart.
________________________________________

7. Conclusion
The project highlights the importance of analyzing customer data to reduce churn. By leveraging OLAP systems, SQL queries, and Power BI, actionable insights were derived, helping the telecommunications company focus on improving customer satisfaction and retention.


