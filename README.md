📊 Modern SQL Data Warehouse Project

📌 Project Overview

This project demonstrates the end-to-end implementation of a Modern Data Warehouse using SQL Server. The warehouse is built using a layered architecture (Bronze → Silver → Gold) and implements a Star Schema for analytical reporting.

The objective of this project is to simulate a real-world data engineering workflow including:

Data ingestion from raw source files

Data cleaning and transformation

Dimensional data modeling

Fact and dimension table creation

Analytical SQL query development

This project showcases practical understanding of Data Warehousing concepts and ETL processes.

🏗️ Architecture

The project follows the Medallion Architecture:

🥉 Bronze Layer – Raw Data

Stores raw CSV data without modification

Acts as staging layer

Preserves original source data

🥈 Silver Layer – Cleaned Data

Data cleansing and standardization

Removed duplicates

Handled null values

Applied validation rules

Converted appropriate data types

🥇 Gold Layer – Business Layer

Implemented Star Schema

Created fact and dimension tables

Optimized for reporting and analytics

🛠️ Tools & Technologies

SQL Server Express

SQL Server Management Studio (SSMS)

T-SQL

Git & GitHub

Draw.io (for schema diagrams)

📂 Project Structure
data-warehouse-project/
│
├── datasets/                           # Raw datasets used for the project (ERP and CRM data)
│
├── docs/                               # Project documentation and architecture details
│   ├── etl.drawio                      # Draw.io file shows all different techniquies and methods of ETL
│   ├── data_architecture.drawio        # Draw.io file shows the project's architecture
│   ├── data_catalog.md                 # Catalog of datasets, including field descriptions and metadata
│   ├── data_flow.drawio                # Draw.io file for the data flow diagram
│   ├── data_models.drawio              # Draw.io file for data models (star schema)
│   ├── naming-conventions.md           # Consistent naming guidelines for tables, columns, and files
│
├── scripts/                            # SQL scripts for ETL and transformations
│   ├── bronze/                         # Scripts for extracting and loading raw data
│   ├── silver/                         # Scripts for cleaning and transforming data
│   ├── gold/                           # Scripts for creating analytical models
│
├── tests/                              # Test scripts and quality files
│
├── README.md                           # Project overview and instructions
├── LICENSE                             # License information for the repository
├── .gitignore                          # Files and directories to be ignored by Git
└── requirements.txt                    # Dependencies and requirements for the project

🔄 ETL Process
Step 1 – Data Ingestion (Bronze)

Loaded raw CSV files using BULK INSERT

Created staging tables

Maintained raw data integrity

Step 2 – Data Transformation (Silver)

Removed duplicate records

Standardized date formats

Cleaned inconsistent values

Applied business transformation rules

Step 3 – Data Modeling (Gold)

Designed Star Schema

Created dimension tables:

dim_customer

dim_product

dim_date

Created fact table:

fact_sales

Implemented primary and foreign key relationships

⭐ Data Model

The final schema consists of:

Fact Table

fact_sales – stores transactional sales data

Dimension Tables

dim_customer – customer details

dim_product – product information

dim_date – calendar attributes

The schema supports efficient aggregation and analytical reporting.

📊 Sample Analytical Queries
Total Sales by Product
SELECT 
    p.product_name,
    SUM(f.sales_amount) AS total_sales
FROM gold.fact_sales f
JOIN gold.dim_product p 
    ON f.product_id = p.product_id
GROUP BY p.product_name
ORDER BY total_sales DESC;

Monthly Sales Trend
SELECT 
    d.year,
    d.month,
    SUM(f.sales_amount) AS monthly_sales
FROM gold.fact_sales f
JOIN gold.dim_date d 
    ON f.date_id = d.date_id
GROUP BY d.year, d.month
ORDER BY d.year, d.month;

📈 Key Learnings

Understanding layered data warehouse architecture

Implementing ETL pipelines using SQL

Designing star schema for analytical systems

Writing optimized SQL queries

Importance of data quality in analytics

🚀 Future Enhancements

Implement Slowly Changing Dimensions (SCD Type 2)

Automate ETL using SQL Server Agent

Add incremental loading

Integrate with Power BI for dashboard creation

Implement data validation checks

👩‍💻 Author

Konda Preksha
B.Tech CSE
Aspiring Data Engineer
