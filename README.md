
# 📊 Modern SQL Data Warehouse Project

## 📌 Project Overview

This project demonstrates the end-to-end implementation of a Modern Data Warehouse using SQL Server. The warehouse is built using a layered architecture (Bronze → Silver → Gold) and implements a Star Schema for analytical reporting.

The objective of this project is to simulate a real-world data engineering workflow including:

- Data ingestion from raw source files  
- Data cleaning and transformation  
- Dimensional data modeling  
- Fact and dimension table creation  
- Analytical SQL query development  

This project showcases practical understanding of Data Warehousing concepts and ETL processes.

---

## 🏗️ Architecture

The project follows the Medallion Architecture:

### 🥉 Bronze Layer – Raw Data
- Stores raw CSV data without modification  
- Acts as staging layer  
- Preserves original source data  

### 🥈 Silver Layer – Cleaned Data
- Data cleansing and standardization  
- Removed duplicates  
- Handled null values  
- Applied validation rules  
- Converted appropriate data types  

### 🥇 Gold Layer – Business Layer
- Implemented Star Schema  
- Created fact and dimension tables  
- Optimized for reporting and analytics  

---

## 🛠️ Tools & Technologies

- SQL Server Express  
- SQL Server Management Studio (SSMS)  
- T-SQL  
- Git & GitHub  
- Draw.io (for schema diagrams)  

---

## 📂 Project Structure

data-warehouse-project/
│
├── datasets/                # Raw CSV files
├── scripts/
│   ├── bronze/              # Data ingestion scripts
│   ├── silver/              # Data transformation scripts
│   ├── gold/                # Fact & dimension table creation
│
├── docs/                    # Architecture & data model diagrams
├── README.md

---

## 🔄 ETL Process

### Step 1 – Data Ingestion (Bronze)
- Loaded raw CSV files using BULK INSERT  
- Created staging tables  
- Maintained raw data integrity  

### Step 2 – Data Transformation (Silver)
- Removed duplicate records  
- Standardized date formats  
- Cleaned inconsistent values  
- Applied business transformation rules  

### Step 3 – Data Modeling (Gold)
- Designed Star Schema  
- Created dimension tables:
  - dim_customer  
  - dim_product  
  - dim_date  
- Created fact table:
  - fact_sales  
- Implemented primary and foreign key relationships  

---

## ⭐ Data Model

Fact Table:
- fact_sales – stores transactional sales data  

Dimension Tables:
- dim_customer – customer details  
- dim_product – product information  
- dim_date – calendar attributes  

The schema supports efficient aggregation and analytical reporting.

---

## 📊 Sample Analytical Query

```sql
SELECT 
    p.product_name,
    SUM(f.sales_amount) AS total_sales
FROM gold.fact_sales f
JOIN gold.dim_product p 
    ON f.product_id = p.product_id
GROUP BY p.product_name
ORDER BY total_sales DESC;
```

---

## 





