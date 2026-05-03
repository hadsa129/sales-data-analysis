# Sales Data Analysis & Data Warehouse Project

Welcome to the **Sales Data Analysis & Data Warehouse Project** repository! 🚀  
This project demonstrates a comprehensive data warehousing and analytics solution for sales data, from building a modern data warehouse to generating actionable business insights. Designed as a portfolio project, it highlights industry best practices in data engineering, data modeling, and business analytics.

---

## 🏗️ Data Architecture

The data architecture follows the **Medallion Architecture** with Bronze, Silver, and Gold layers:

![Data Pipeline Architecture](docs/data-pipeline-architecture.png)

### Architecture Layers

1. **Bronze Layer**: Stores raw data as-is from source systems (ERP and CRM CSV files)
2. **Silver Layer**: Data cleansing, standardization, and normalization processes
3. **Gold Layer**: Business-ready data modeled into star schema for analytics and reporting

![Data Model](docs/data_model.png)

### Data Flow

![Data Flow](docs/data_flow.png)

---
## 📖 Project Overview

This project involves:

1. **Data Architecture**: Designing a Modern Data Warehouse Using Medallion Architecture **Bronze**, **Silver**, and **Gold** layers.
2. **ETL Pipelines**: Extracting, transforming, and loading data from source systems into the warehouse.
3. **Data Modeling**: Developing fact and dimension tables optimized for analytical queries.
4. **Analytics & Reporting**: Creating SQL-based reports and dashboards for actionable insights.

🎯 This repository is an excellent resource for professionals and students looking to showcase expertise in:
- SQL Development
- Data Architecture
- Data Engineering  
- ETL Pipeline Development  
- Data Modeling  
- Business Analytics  

---

## 📊 Gold Layer Data Catalog

The Gold Layer represents the business-level data structured for analytical and reporting use cases. It follows a star schema with dimension tables and fact tables optimized for business intelligence.

### 🏪 Dimension Tables

#### **gold.dim_customers**
**Purpose**: Stores comprehensive customer details enriched with demographic and geographic data for customer analytics and segmentation.

| Column Name      | Data Type     | Description                                                                                   |
|------------------|---------------|-----------------------------------------------------------------------------------------------|
| customer_key     | INT           | Surrogate key uniquely identifying each customer record in the dimension table.               |
| customer_id      | INT           | Unique numerical identifier assigned to each customer.                                        |
| customer_number  | NVARCHAR(50)  | Alphanumeric identifier representing the customer, used for tracking and referencing.         |
| first_name       | NVARCHAR(50)  | The customer's first name, as recorded in the system.                                         |
| last_name        | NVARCHAR(50)  | The customer's last name or family name.                                                     |
| country          | NVARCHAR(50)  | The country of residence for the customer (e.g., 'Australia').                               |
| marital_status   | NVARCHAR(50)  | The marital status of the customer (e.g., 'Married', 'Single').                              |
| gender           | NVARCHAR(50)  | The gender of the customer (e.g., 'Male', 'Female', 'n/a').                                  |
| birthdate        | DATE          | The date of birth of the customer, formatted as YYYY-MM-DD (e.g., 1971-10-06).               |
| create_date      | DATE          | The date and time when the customer record was created in the system.                         |

#### **gold.dim_products**
**Purpose**: Provides detailed product information including attributes, categories, and pricing for product performance analysis.

| Column Name         | Data Type     | Description                                                                                   |
|---------------------|---------------|-----------------------------------------------------------------------------------------------|
| product_key         | INT           | Surrogate key uniquely identifying each product record in the product dimension table.         |
| product_id          | INT           | A unique identifier assigned to the product for internal tracking and referencing.            |
| product_number      | NVARCHAR(50)  | A structured alphanumeric code representing the product, often used for categorization or inventory. |
| product_name        | NVARCHAR(50)  | Descriptive name of the product, including key details such as type, color, and size.         |
| category_id         | NVARCHAR(50)  | A unique identifier for the product's category, linking to its high-level classification.     |
| category            | NVARCHAR(50)  | The broader classification of the product (e.g., Bikes, Components) to group related items.  |
| subcategory         | NVARCHAR(50)  | A more detailed classification of the product within the category, such as product type.      |
| maintenance_required| NVARCHAR(50)  | Indicates whether the product requires maintenance (e.g., 'Yes', 'No').                       |
| cost                | INT           | The cost or base price of the product, measured in monetary units.                            |
| product_line        | NVARCHAR(50)  | The specific product line or series to which the product belongs (e.g., Road, Mountain).      |
| start_date          | DATE          | The date when the product became available for sale or use.                                   |

### 💰 Fact Tables

#### **gold.fact_sales**
**Purpose**: Stores transactional sales data for comprehensive sales analytics, revenue tracking, and business performance metrics.

| Column Name     | Data Type     | Description                                                                                   |
|-----------------|---------------|-----------------------------------------------------------------------------------------------|
| order_number    | NVARCHAR(50)  | A unique alphanumeric identifier for each sales order (e.g., 'SO54496').                      |
| product_key     | INT           | Surrogate key linking the order to the product dimension table.                               |
| customer_key    | INT           | Surrogate key linking the order to the customer dimension table.                              |
| order_date      | DATE          | The date when the order was placed.                                                           |
| shipping_date   | DATE          | The date when the order was shipped to the customer.                                          |
| due_date        | DATE          | The date when the order payment was due.                                                      |
| sales_amount    | INT           | The total monetary value of the sale for the line item, in whole currency units (e.g., 25).   |
| quantity        | INT           | The number of units of the product ordered for the line item (e.g., 1).                       |
| price           | INT           | The price per unit of the product for the line item, in whole currency units (e.g., 25).      |

---

## 📈 Analytics Capabilities

This data model enables comprehensive business analytics across multiple dimensions:

### Customer Analytics
- Customer segmentation by demographics and geography
- Customer lifetime value analysis
- Purchase behavior patterns
- Customer retention and churn analysis

### Product Performance
- Sales performance by product categories and subcategories
- Product profitability analysis
- Inventory and maintenance requirements tracking
- Product line performance comparison

### Sales Analytics
- Revenue trends and seasonality analysis
- Sales cycle analysis (order to shipping time)
- Payment due date compliance tracking
- Order quantity and price distribution analysis

---


---

## 🚀 Project Requirements

### Building the Data Warehouse (Data Engineering)

#### Objective
Develop a modern data warehouse using SQL Server to consolidate sales data, enabling analytical reporting and informed decision-making.

#### Specifications
- **Data Sources**: Import data from two source systems (ERP and CRM) provided as CSV files.
- **Data Quality**: Cleanse and resolve data quality issues prior to analysis.
- **Integration**: Combine both sources into a single, user-friendly data model designed for analytical queries.
- **Scope**: Focus on the latest dataset only; historization of data is not required.
- **Documentation**: Provide clear documentation of the data model to support both business stakeholders and analytics teams.

---

### BI: Analytics & Reporting (Data Analysis)

#### Objective
Develop SQL-based analytics to deliver detailed insights into:
- **Customer Behavior**
- **Product Performance**
- **Sales Trends**

These insights empower stakeholders with key business metrics, enabling strategic decision-making.  

For more details, refer to [docs/requirements.md](docs/requirements.md).

---

## 🛠️ Installation & Setup

### Prerequisites
- SQL Server (2019 or later)
- SQL Server Management Studio (SSMS) or similar SQL client
- Python 3.8+ (for running ETL scripts, optional)

### Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/sales-data-analysis.git
   cd sales-data-analysis
   ```

2. **Set up the database**
   ```sql
   -- Create the database
   CREATE DATABASE SalesDataWarehouse;
   GO
   
   USE SalesDataWarehouse;
   GO
   ```

3. **Run the ETL scripts in order**
   ```bash
   # Bronze Layer - Load raw data
   sqlcmd -S your-server -d SalesDataWarehouse -i scripts/bronze/load_raw_data.sql
   
   # Silver Layer - Clean and transform
   sqlcmd -S your-server -d SalesDataWarehouse -i scripts/silver/clean_transform_data.sql
   
   # Gold Layer - Create analytical model
   sqlcmd -S your-server -d SalesDataWarehouse -i scripts/gold/create_analytical_model.sql
   ```

4. **Verify the setup**
   ```sql
   -- Check Gold layer tables
   SELECT COUNT(*) AS customer_count FROM gold.dim_customers;
   SELECT COUNT(*) AS product_count FROM gold.dim_products;
   SELECT COUNT(*) AS sales_count FROM gold.fact_sales;
   ```

---

## � Analytics & Insights

### Business Intelligence Capabilities

The Gold Layer data model enables comprehensive business analytics across multiple dimensions:

#### 🏪 Customer Analytics
- **Customer Segmentation**: Analyze customer demographics and geographic distribution
- **Customer Lifetime Value**: Track customer spending patterns over time
- **Purchase Behavior**: Identify buying patterns and preferences
- **Customer Retention**: Monitor customer loyalty and churn metrics

#### 📦 Product Performance
- **Sales Performance**: Track product sales by categories and subcategories
- **Product Profitability**: Analyze margins and cost structures
- **Inventory Insights**: Monitor maintenance requirements and stock levels
- **Product Line Analysis**: Compare performance across different product lines

#### 💰 Sales Analytics
- **Revenue Trends**: Analyze seasonal patterns and growth trends
- **Sales Cycle Analysis**: Track order processing and shipping times
- **Payment Compliance**: Monitor due date adherence
- **Order Analysis**: Understand quantity and price distributions

### Data Analysis Workflow

![Data Analysis Steps](docs/data_abalysis_steps.png)

---

## 🔄 Data Integration Process

### ETL Pipeline Architecture

The project implements a comprehensive data integration process that transforms raw data into actionable business insights:

![Data Integration](docs/data_integration.png)

### Key Features
- **Automated Data Loading**: Streamlined ingestion from ERP and CRM systems
- **Data Quality Assurance**: Built-in validation and cleansing mechanisms
- **Scalable Architecture**: Designed to handle growing data volumes
- **Real-time Processing**: Support for near real-time analytics

---

## 📂 Repository Structure
```
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
```
---

## ☕ Stay Connected

Let's stay in touch! Feel free to connect with me on the following platforms:

[![YouTube](https://img.shields.io/badge/YouTube-red?style=for-the-badge&logo=youtube&logoColor=white)](http://bit.ly/3GiCVUE)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/baraa-khatib-salkini)
[![Website](https://img.shields.io/badge/Website-000000?style=for-the-badge&logo=google-chrome&logoColor=white)](https://www.datawithbaraa.com)
[![Newsletter](https://img.shields.io/badge/Newsletter-FF5722?style=for-the-badge&logo=substack&logoColor=white)](https://bit.ly/BaraaNewsletter)
[![PayPal](https://img.shields.io/badge/PayPal-00457C?style=for-the-badge&logo=paypal&logoColor=white)](https://paypal.me/baraasalkini)
[![Join](https://img.shields.io/badge/Join-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@datawithbaraa)

All Courses and their materials are completely free, and all I ask is your support through subscribing, liking, and commenting on my channel. Your engagement means the world to me and It help the channel!
- ✅ **SQL Full Course:** [Course Link](https://youtu.be/SSKVgrwhzus) | [Download Materials](https://www.datawithbaraa.com/sql-introduction/sql-ultimate-course/) | [GIT Repo](https://github.com/DataWithBaraa/sql-ultimate-course)
- ✅ **Tableau Full Course:** [Course Link](https://www.youtube.com/watch?v=K3pXnbniUcM) | [Download Materials](https://www.datawithbaraa.com/tableau/tableau-thank-you/) | [Public](https://public.tableau.com/app/profile/baraa.salkini/vizzes)

- ✅ **SQL Data Warehouse Project:** [Course Link](https://youtu.be/SSKVgrwhzus) | [Download Materials](https://www.datawithbaraa.com/sql-introduction/advanced-sql-project/) | [GIT Repo](https://github.com/DataWithBaraa/sql-data-warehouse-project)
- ✅ **SQL Exploratory Data Analysis Project:** [Course Link](https://youtu.be/SSKVgrwhzus) | [Download Materials](https://www.datawithbaraa.com/sql-introduction/advanced-sql-analytics-project/) | [GIT Repo](https://github.com/DataWithBaraa/sql-data-analytics-project)
- ✅ **SQL Advanced Data Analysis Project:** [Course Link](https://youtu.be/SSKVgrwhzus) | [Download Materials](https://www.datawithbaraa.com/sql-introduction/advanced-sql-analytics-project/) | [GIT Repo](https://github.com/DataWithBaraa/sql-data-analytics-project)
  
- ✅ **Tableau Sales Project:** [Course Link](https://www.youtube.com/watch?v=dahrmqT5GD4) | [Download Materials](https://datawithbaraa.substack.com/p/access-to-course-materials) | [Public](https://public.tableau.com/app/profile/baraa.salkini/vizzes)
- ✅ **Tableau HR Project:** [Course Link](https://www.youtube.com/watch?v=UcGF09Awm4Y) | [Download Materials](https://datawithbaraa.substack.com/p/access-to-course-materials) | [Public](https://public.tableau.com/app/profile/baraa.salkini/vizzes)
- ✅ **ChatGPT:** [Course Link](https://www.youtube.com/watch?v=LJLNfei4i-c) | [Download Materials](https://datawithbaraa.substack.com/p/access-to-course-materials)

---

## 🛡️ License

This project is licensed under the [MIT License](LICENSE). You are free to use, modify, and share this project with proper attribution.

## 🌟 About Me

Hi there! I'm **Baraa Khatib Salkini**, also known as **Data With Baraa**. I’m an IT professional and passionate YouTuber on a mission to share knowledge and make working with data enjoyable and engaging!

Let's stay in touch! Feel free to connect with me on the following platforms:

[![YouTube](https://img.shields.io/badge/YouTube-red?style=for-the-badge&logo=youtube&logoColor=white)](http://bit.ly/3GiCVUE)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/baraa-khatib-salkini)
[![Website](https://img.shields.io/badge/Website-000000?style=for-the-badge&logo=google-chrome&logoColor=white)](https://www.datawithbaraa.com)
[![Newsletter](https://img.shields.io/badge/Newsletter-FF5722?style=for-the-badge&logo=substack&logoColor=white)](https://bit.ly/BaraaNewsletter)
[![PayPal](https://img.shields.io/badge/PayPal-00457C?style=for-the-badge&logo=paypal&logoColor=white)](https://paypal.me/baraasalkini)
[![Join](https://img.shields.io/badge/Join-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@datawithbaraa)
