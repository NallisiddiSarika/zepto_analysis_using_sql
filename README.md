# zepto_analysis_using_sql
This is a real-world data analyst project based on an e-commerce inventory dataset scraped from Zepto — one of India’s fastest-growing quick-commerce startups. This project simulates real analyst workflows, from raw data exploration to business-focused data analysis.

# Overview
The objective of the project is to finding the real business insights using SQL. It includes the following:

✅ Set up a messy, real-world e-commerce inventory database
✅ Perform Exploratory Data Analysis (EDA) to explore product categories, availability, and pricing inconsistencies
✅ Implement Data Cleaning to handle null values, remove invalid entries, and convert pricing from paise to rupees
✅ Write business-driven SQL queries to derive insights around pricing, inventory, stock availability, revenue and more

# Dataset
The dataset was sourced from Kaggle and was originally scraped from Zepto’s official product listings.
Each row represents a unique SKU (Stock Keeping Unit) for a product. Duplicate product names exist because the same product may appear multiple times in different package sizes, weights, discounts, or categories to improve visibility – exactly how real catalog data looks.

**Columns:**

i. sku_id: Unique identifier for each product entry (Synthetic Primary Key)

ii. name: Product name as it appears on the app

iii. category: Product category like Fruits, Snacks, Beverages, etc.

iv. mrp: Maximum Retail Price (originally in paise, converted to ₹)

v. discountPercent: Discount applied on MRP

vi. discountedSellingPrice: Final price after discount (also converted to ₹)

vii. availableQuantity: Units available in inventory

viii. weightInGms: Product weight in grams

ix. outOfStock: Boolean flag indicating stock availability

x. quantity: Number of units per package (mixed with grams for loose produce)

# Tools & Technologies

- PostgreSQL – Database management
- SQL – Data querying and analysis
- pgAdmin – PostgreSQL GUI tool
- CSV Dataset – Source data file

# Project Steps

Here’s a step-by-step breakdown of what we do in this project:
**1. Database and Table Creation**
As start of the project , first created a database and table.

    create table zepto(
sku_id SERIAL PRIMARY KEY,
category VARCHAR(120),
name VARCHAR(150) NOT NULL,
mrp NUMERIC(8,2),
discountPercent NUMERIC(5,2),
availableQuantity INTEGER,
discountedSellingPrice NUMERIC(8,2),
weightInGms INTEGER,
outOfStock BOOLEAN,
quantity INTEGER
);

**2. Data Import**
- Loaded CSV using pgAdmin's import feature.
- Faced encoding issues (UTF-8 error), which were fixed by saving the CSV file using CSV UTF-8 format.

**3. Data Exploration**
- Counted the total number of records in the dataset
- Viewed a sample of the dataset to understand structure and content
- Checked for null values across all columns
- Identified distinct product categories available in the dataset
- Compared in-stock vs out-of-stock product counts
- Detected products present multiple times, representing different SKUs

**4. Data Cleaning**
- Identified and removed rows where MRP or discounted selling price was zero
- Converted mrp and discountedSellingPrice from paise to rupees for consistency and readability

**5. Business Insights**
1. Found top 10 best-value products based on discount percentage
2. Identified high-MRP products that are currently out of stock
3. Estimated potential revenue for each product category
4. Filtered expensive products (MRP > ₹500) with minimal discount
5. Ranked top 5 categories offering highest average discounts
6. Calculated price per gram to identify value-for-money products
7. Grouped products based on weight into Low, Medium, and Bulk categories
8. Measured total inventory weight per product category



