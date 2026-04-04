# 📘 Project Step-by-Step Documentation

---

## 🔹 Step 1: Azure Resource Setup

* Created Resource Group: **rg-ecommerce-project**
* Created Azure services:

  * Storage Account (ADLS Gen2)
  * Azure SQL Server & Database
  * Azure Databricks Workspace
  * Azure Data Factory
  * Access Connector for Databricks

<img width="1915" height="1027" alt="01_Azure_Interface" src="https://github.com/user-attachments/assets/b47ca0ea-3fc8-4942-b940-71be3bb5793c" />


---

## 🔹 Step 2: Data Storage Setup (ADLS)

* Created container: **projectstorage**
* Created folders:

  * bronze (raw data)
  * silver (cleaned data)
  * gold (business data)
  * metastore (for Unity Catalog)

<img width="1917" height="1028" alt="03_Azure_Storage_Container" src="https://github.com/user-attachments/assets/43f3390a-b69c-4d3b-b70e-e1f40fcd70cc" />


---

## 🔹 Step 3: Source 1 – Orders Data (CSV)

* Loaded Ecommerce.csv into Databricks
* Read data using PySpark
* Created temporary view for SQL operations

<img width="1918" height="1032" alt="04_Azure_Storage_Directory" src="https://github.com/user-attachments/assets/6b8d2acc-c511-4685-9db5-13f309c1cd3c" />

---

## 🔹 Step 4: Source 2 – Customers Data (SQL)

* Extracted customer data from orders dataset
* Selected required columns:

  * customer_id
  * customer_name
  * city
* Loaded data into Azure SQL Database using JDBC

<img width="1917" height="1028" alt="06_Azure_SQL_database" src="https://github.com/user-attachments/assets/2002895b-ef63-409d-9b84-94a96e85a3ef" />

---

## 🔹 Step 5: Data Ingestion using ADF

* Created ADF pipeline
* Used Copy Activity to move data:

  * Source → ADLS Bronze layer
* Connected Databricks notebooks in pipeline

📸 Screenshot:
(Add ADF pipeline design screenshot)

---

## 🔹 Step 6: Databricks Setup (Unity Catalog)

* Created Access Connector
* Configured Unity Catalog (metastore)
* Created:

  * External Locations (bronze, silver, gold)
  * Catalog: ecommerce
  * Schemas: bronze, silver, gold

<img width="1918" height="1032" alt="08_Azure_Databricks" src="https://github.com/user-attachments/assets/ad1336c9-ea61-4d41-b624-e5b21424b9e9" />


---

## 🔹 Step 7: Bronze Layer (Raw Data)

* Loaded raw data from ADLS
* Created Delta tables:

  * orders
  * customers
* No transformations applied


---

## 🔹 Step 8: Silver Layer (Data Cleaning)

Performed data cleaning:

* Removed duplicates (OrderID)
* Filtered invalid records
* Trimmed spaces
* Standardized text (Proper case)
* Converted date format
* Validated numeric columns
* Removed duplicate customers using window function


---

## 🔹 Step 9: Gold Layer (Business Layer)

* Joined orders and customers using customer_id
* Created business-level tables

📊 KPIs Created:

* Total Revenue
* Total Orders
* Revenue by Category
* Revenue by City
* Monthly Revenue Trend
* Average Order Value
* Top Customers
* Payment Analysis
* Return Analysis


---

## 🔹 Step 10: Reporting Layer

* Created **unified reporting table**
* Combined all important business metrics
* Prepared final dataset for dashboard



---

## 🔹 Step 11: Pipeline Orchestration

* Built end-to-end pipeline in ADF:

  * Data Ingestion
  * Data Transformation
  * Reporting Layer
* Automated full workflow

<img width="1918" height="1026" alt="10_Data_factory_Orchestration" src="https://github.com/user-attachments/assets/f92088c0-96bc-4e92-981f-58fe1a76b20a" />


---

## 🔹 Step 12: Power BI Dashboard

* Created interactive dashboard
* Visualized:

  * Revenue
  * Orders
  * Customer insights
  * Trends and KPIs

<img width="1392" height="803" alt="12_Dashboard_Screenshot" src="https://github.com/user-attachments/assets/1f4a7632-0d86-4a28-af4d-652bb1857e75" />
<img width="1442" height="810" alt="13_Dashboard_Screenshot" src="https://github.com/user-attachments/assets/c3c01399-70bc-427e-a301-a8a2655f57b0" />
<img width="1433" height="805" alt="14_Dashboard_Screenshot" src="https://github.com/user-attachments/assets/43ae7a0e-d9d4-4736-8782-6c052a9c6240" />


---

## ✅ Final Outcome

* Built end-to-end data pipeline
* Integrated multiple data sources
* Implemented Medallion Architecture
* Generated business insights
* Automated pipeline using ADF
