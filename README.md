# Building an E-commerce Data Warehouse Using Hive

## Overview
This project demonstrates a step-by-step implementation of an e-commerce data warehouse using Apache Hive on a Hadoop cluster. The warehouse is designed to store, process, and analyze e-commerce transaction data, enabling businesses to derive valuable insights from their sales information. By following this guide, you can create a scalable, efficient data warehouse infrastructure for handling large volumes of e-commerce data.

## Project Components

### Technologies Used
- **Apache Hadoop**: Distributed storage and processing framework
- **Apache Hive**: Data warehouse infrastructure built on top of Hadoop
- **HDFS (Hadoop Distributed File System)**: Storage layer for the data
- **HiveQL**: SQL-like query language for data manipulation and analysis
- **Cloudera Environment**: Integrated platform for Hadoop ecosystem components

### Dataset Information
The project utilizes a sample e-commerce dataset from Kaggle containing transaction information with the following structure:
- InvoiceNo: Unique identifier for each transaction
- CompanyName: Company or customer name
- StockCode: Product code
- Quantity: Number of units purchased
- InvoiceDate: Date of the transaction
- UnitPrice: Price per unit of the product
- CustomerID: Unique identifier for each customer
- Country: Country where the transaction originated

## Implementation Guide

### Step 1: Environment Setup
The project begins with setting up the Cloudera environment and starting the necessary Hadoop services:
- HDFS Datanode and Namenode
- YARN ResourceManager and NodeManager

This ensures that the distributed storage and processing framework is ready for data ingestion and analysis.

### Step 2: Data Ingestion
The process continues with downloading a sample e-commerce dataset from Kaggle and uploading it to HDFS, creating a dedicated directory structure for the warehouse.

### Step 3-4: Hive Configuration
The guide includes instructions for starting Hive and creating a dedicated database for the e-commerce data warehouse, establishing a logical separation from other data sources.

### Step 5: Schema Definition
A detailed schema is defined for the external table that maps to the raw CSV data, specifying column names, data types, and the delimiter used in the source file.

### Step 6-7: Data Exploration
Initial exploration queries are provided to help understand the dataset structure and perform basic counts and validations of the imported data.

### Step 8: Data Cleaning
The implementation includes data transformation steps to ensure data quality, such as removing duplicate entries through Hive's INSERT OVERWRITE capability.

### Step 9: Data Loading
Instructions for creating optimized internal tables that transform the raw data into a more usable format, renaming columns for clarity and better semantic meaning.

### Step 10: Advanced Analytics
The project culminates with advanced analytics capabilities, including:
- Revenue calculations
- Table partitioning by date for improved query performance
- Filtering data by various criteria (date range, customer ID)
- Performing aggregations (sum, average) for business insights

## Usage Examples

### Basic Queries
```sql
-- View sample data
SELECT * FROM ecommerce_data LIMIT 5;

-- Count total records
SELECT COUNT(*) FROM ecommerce_data;
```

### Data Transformations
```sql
-- Remove duplicates
INSERT OVERWRITE TABLE ecommerce_data
SELECT DISTINCT * FROM ecommerce_data;
```

### Advanced Analytics
```sql
-- Calculate total revenue
SELECT SUM(UnitPrice * Quantity) AS total_revenue
FROM ecommerce_data;

-- Find average unit price
SELECT AVG(UnitPrice) AS avg_unit_price
FROM ecommerce_data;
```

### Optimized Queries with Partitioning
```sql
-- Query data from a specific date partition
SELECT * FROM ecommerce_partitioned
WHERE order_date = '2023-09-15';
```

## Benefits and Applications

### Business Intelligence
- **Sales Analysis**: Understand sales trends across different time periods
- **Customer Segmentation**: Analyze purchasing patterns by customer or region
- **Inventory Management**: Identify top-selling products and optimize stock levels

### Performance Optimization
- **Partitioning**: Improves query performance by dividing data into manageable chunks
- **ORC Format**: Provides efficient storage and faster query execution compared to raw CSV files
- **Schema Evolution**: Supports adding new data fields without disrupting existing analytics

### Scalability
The data warehouse architecture is designed to scale horizontally, accommodating growing data volumes without significant performance degradation.

## System Requirements
- Cloudera environment or similar Hadoop distribution
- Minimum 8GB RAM recommended
- Sufficient disk space for HDFS storage
- Java Runtime Environment (JRE)

## Conclusion
This e-commerce data warehouse project using Hive demonstrates a comprehensive approach to building a scalable analytics platform. By following the step-by-step guide, organizations can implement similar solutions for their e-commerce data analysis needs, enabling data-driven decision-making and business insights.

The project showcases fundamental data warehousing concepts including data ingestion, schema definition, transformation, and analytics, all implemented using open-source technologies in the Hadoop ecosystem.

---

Developed by Keyur Rajput
