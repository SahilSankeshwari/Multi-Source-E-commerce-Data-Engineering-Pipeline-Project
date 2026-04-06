#  Multi-Source E-Commerce Data Engineering Pipeline

##  Overview

This project is an end-to-end data engineering pipeline built using Azure services.

The main goal is to collect data from multiple sources, process it using Databricks, and generate business insights for reporting.

---

##  Data Sources

1. **Source 1 (SFTP / CSV)**

   * E-commerce orders data (Ecommerce.csv)

2. **Source 2 (Azure SQL Database)**

   * Customers table created using Databricks
   * Extracted required columns:

     * customer_id
     * customer_name
     * city

---

##  Tools & Technologies

* Azure Data Factory (ADF)
* Azure Data Lake Storage (ADLS Gen2)
* Azure Databricks (PySpark)
* Azure SQL Database
* Unity Catalog
* Delta Lake
* Power BI

---

##  Architecture (Medallion)

The project follows Medallion Architecture:

* **Bronze Layer** → Raw Data
* **Silver Layer** → Cleaned Data
* **Gold Layer** → Business Data

---

##  Project Workflow

### 1. Source Creation

* Loaded CSV into Databricks
* Extracted customer data
* Created customer table in Azure SQL using JDBC

---

### 2. Data Ingestion (ADF)

* Used Azure Data Factory
* Copied data from:
  
  * SQL → ADLS
* Stored in **Bronze layer**

---

### 3. Bronze Layer (Raw Data)

* Stored raw data without changes
* Created Delta tables:

  * orders
  * customers

---

### 4. Silver Layer (Data Cleaning)

Performed data cleaning and transformation:

* Removed duplicates (OrderID)
* Removed invalid records
* Trimmed spaces
* Standardized text (Proper case)
* Converted date format
* Validated numeric values
* Handled duplicates in customers using window function


---

### 5. Gold Layer (Business Layer)

* Joined orders and customers using **customer_id**
* Created **business KPIs**

####  KPIs Created:

* Total Revenue
* Total Orders
* Revenue by Category
* Revenue by City
* Monthly Revenue Trend
* Average Order Value
* Top Customers
* Payment Method Analysis
* Return Analysis

---

### 6. Final Reporting Table

* Created a **unified reporting table**
* Combined all important metrics
* Used for Power BI dashboard

---

### 7. Data Governance

* Configured Unity Catalog
* Created:

  * External Locations
  * Catalog
  * Schemas (bronze, silver, gold)

---

### 8. Pipeline Orchestration

* Built pipeline using ADF:

  * Data Ingestion
  * Data Transformation
  * Reporting Layer
* Automated full workflow

---

### 9. Dashboard (Power BI)

* Created interactive dashboard:

  * Revenue insights
  * Customer analysis
  * Trends and KPIs

---

##  Key Highlights

* Multi-source data integration
* End-to-end pipeline
* Medallion Architecture
* Real-time scalable design
* Business-driven KPIs
* Automated pipeline

---

##  Conclusion

This project demonstrates building a complete data engineering pipeline from raw data ingestion to business reporting using Azure tools.


