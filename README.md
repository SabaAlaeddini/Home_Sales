# Home_Sales
Module 22 Challenge
## Home Sales Analysis with SparkSQL
# Overview
This project leverages SparkSQL to analyze home sales data and extract key insights efficiently. Using PySpark, we process and query large datasets to explore home prices based on bedrooms, bathrooms, square footage, view ratings, and more.

# Setup & Data Processing
- Imported necessary PySpark SQL functions.
- Read home_sales_revised.csv from an AWS S3 bucket into a PySpark DataFrame.
- Created a temporary table (home_sales) for SQL-based queries.

# Data Analysis with SparkSQL
Executed SQL queries to determine:

1. Average price of four-bedroom houses sold per year.
2. Average price of three-bed, three-bath homes per year built.
3. Average price of homes (3 beds, 3 baths, 2 floors, ≥ 2,000 sq ft) per year built.
4. Average home price per "view" rating, filtering for prices ≥ $350,000 (including runtime analysis).

# Performance Optimization
- Cached the home_sales table and compared query runtime with uncached data.
- Partitioned the dataset by date_built and stored it in Parquet format for efficiency.
- Created a temporary table for the Parquet data and reran queries for runtime comparison.
- Uncached the home_sales table and verified its removal.

# Key Findings
- Caching (0.44s) was the fastest, retrieving data from memory.
- Partitioning (0.87s) improved performance by reducing scanned data but was slower than caching.
- Uncached query (1.18s) took the longest due to full dataset scans.
- Conclusion: Caching is best for repeated queries, while partitioning optimizes storage and retrieval.

# Technologies Used
- Apache Spark (PySpark)
- SparkSQL for querying structured data
- Parquet for optimized storage
- Google Colab & Jupyter Notebook for execution
