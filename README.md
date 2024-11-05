# **🚀 Customer Retention Automated Pipeline 📈 AWS S3, Glue, Redshift, Athena & Power BI 🛠️**

Welcome to the **Customer Churn Analysis Pipeline** repository! This project demonstrates an end-to-end data pipeline using AWS Glue, Amazon S3, Amazon Redshift, Apache Airflow, and Power BI. 

The objective is to extract customer churn data, load it into a Redshift database, orchestrate the workflow with Apache Airflow, and visualize insights using Power BI.
This pipeline is designed to showcase real-world data engineering and analytics practices.

![Customer Churn Data Analytics drawio](https://github.com/user-attachments/assets/d5047834-ebdb-4e34-8f80-f9918693cd50)



## 📖 Project Overview

This project involves creating a data pipeline to analyze customer churn using AWS services. The dataset includes customer information and their service subscription status, providing insights into churn trends and reasons. 

We integrate multiple AWS services to build this pipeline, automate workflows, and visualize data with Power BI.

## ✨ Features
- **Automated Data Ingestion**: Data is extracted from Amazon S3 and loaded into Amazon Redshift. 🗂️
- **Orchestrated Workflow**: Apache Airflow automates and schedules data tasks. ⏲️
- **Data Transformation and Cleansing**: AWS Glue jobs are used for data cleaning and transformation. 🧼
- **Data Visualization**: Power BI connects to Redshift for real-time data visualization. 📊

## 🏛️ Architecture

The project follows this architecture:
1. **Amazon S3 (Data Storage) 🗄️**: Stores raw data (CSV files).
2. **AWS Glue (Data Cataloging and ETL) 🕵️‍♂️**: Crawls and catalogs data, performs data transformation.
3. **Amazon Redshift (Data Warehouse) 🏢**: Acts as the data warehouse for structured data storage.
4. **Apache Airflow (Workflow Orchestration) 🌬️**: Orchestrates the ETL process, running tasks on an EC2 instance.
5. **Power BI (Data Visualization) 📊**: Provides interactive dashboards and visualizations of customer churn data.

Refer to the attached workflow diagram for an overview of the data flow. 🖼️

## 🔍 Component Breakdown

### 1. **Amazon S3 (Data Storage) 🗄️**
   - **Function**: Amazon S3 is used as the initial storage location for the raw customer churn data. CSV files containing customer information are uploaded to an S3 bucket, allowing for organized storage and easy accessibility.
   - **Role in Pipeline**: S3 serves as the source layer for data ingestion. All subsequent processes in the pipeline, including crawling, transforming, and loading, rely on accessing this raw data from S3.

### 2. **AWS Glue (Data Cataloging and ETL) 🕵️‍♂️**
   - **Function**: AWS Glue is used to crawl the S3 bucket and create a data catalog that stores metadata about the dataset, such as column names and data types. Glue also performs Extract, Transform, Load (ETL) jobs to clean and prepare the data, making it compatible with Amazon Redshift.
   - **Role in Pipeline**: Glue enables data preparation and transformation by crawling raw data and automatically inferring its schema. This metadata is stored in the Glue Data Catalog, making it discoverable for querying in Redshift or Athena. The ETL jobs transform raw data, handling any data cleansing or formatting required before loading it into Redshift.

### 3. **Amazon Redshift (Data Warehouse) 🏢**
   - **Function**: Amazon Redshift is the data warehousing solution in the pipeline, where transformed data is loaded for long-term storage and analysis. The data is structured in tables, allowing for efficient SQL querying and analytics.
   - **Role in Pipeline**: Redshift acts as the central storage location for processed data. With data stored in a structured format, it enables fast, complex querying across large datasets, making it suitable for customer churn analysis and other analytics. Power BI and other BI tools can connect to Redshift for real-time data access.

### 4. **Apache Airflow (Workflow Orchestration) 🌬️**
   - **Function**: Apache Airflow is a tool for orchestrating and automating data workflows. It schedules and manages tasks like crawling the S3 bucket, running Glue jobs, and loading data into Redshift. Airflow manages these tasks in a Directed Acyclic Graph (DAG) to ensure they execute in the correct order.
   - **Role in Pipeline**: Airflow provides automation, ensuring data is regularly ingested, transformed, and loaded without manual intervention. It allows users to define dependencies and timing for each task, ensuring data workflows execute on schedule or in response to events, enabling a continuous, automated data pipeline.

### 5. **Power BI (Data Visualization) 📊**
   - **Function**: Power BI is a business intelligence tool used for creating interactive visualizations and dashboards. In this pipeline, Power BI connects to Amazon Redshift, enabling users to explore and visualize customer churn data.
   - **Role in Pipeline**: Power BI transforms the structured data in Redshift into actionable insights through visualizations like charts and graphs. By providing data access directly from Redshift, Power BI helps users explore trends, patterns, and customer behaviors. These visualizations assist stakeholders in making data-driven decisions, especially around customer retention strategies.

## 📦 Setup Instructions

### Prerequisites
- AWS account with permissions to create S3 buckets, Redshift clusters, Glue jobs, and EC2 instances. 🔐
- Power BI Desktop installed. 🖥️
- Apache Airflow installed on an EC2 instance or local machine. 🌐

### Steps
1. **Data Storage**: Upload the CSV files to an Amazon S3 bucket. 📤
2. **Glue Setup**: Create Glue Crawlers to catalog the data in S3. Set up Glue jobs to clean and transform the data. 🧹
3. **Redshift Configuration**: Create a Redshift cluster and configure permissions for S3 and Glue access. 🔧
4. **Airflow DAG**: Use the provided DAG script to automate ETL tasks with Airflow. 🔄
5. **Data Visualization**: Use Power BI to connect to Redshift and create visualizations. 📈

## ⚙️ Usage

1. **Run Airflow DAG**: Start the Airflow scheduler and trigger the DAG to automate data ingestion and transformation tasks. 🔁
2. **View Data in Redshift**: Check the Redshift tables to verify data has been loaded successfully. ✅
3. **Visualize in Power BI**: Connect Power BI to the Redshift cluster to build customer churn dashboards. 📊

## 📁 File Descriptions

- **`customer_churn_dag.py`**: The Apache Airflow DAG script automates ETL processes, including data crawling, transformation, and loading into Redshift. 📝
- **`requirements.txt`**: Contains Python dependencies needed for the project. Use this file to set up a consistent environment. 📦
- **`README.md`**: Documentation for setting up and running the project. 📄
- **`Telco_customer_churn.csv`, `Telco_customer_churn1.csv`, `Telco_customer_churn2.csv`, `Telco_customer_churn3.csv`**: Sample datasets used for analyzing customer churn. 📂

## 📊 Dataset

The dataset contains customer data with attributes such as customer demographics, subscription status, contract types, payment methods, and churn indicators. This data is available on Kaggle under "Telco Customer Churn." 📊

## 📈 Visualization

Use Power BI to connect to the Redshift cluster and visualize the following insights:
- **Churn Reasons**: Analyze why customers are churning (e.g., support issues, competitor pricing). ❓
- **Customer Demographics**: Explore churn patterns by age group, location, and gender. 👤
- **Subscription Breakdown**: Visualize customer subscriptions across different services. 📈

### Example visualizations:
- Bar charts showing customer count by churn status and demographic attributes. 📊
- Pie charts depicting payment method preferences among customers. 🥧
- Histograms of customer tenure by service type. 📉

## 📋 Dependencies

Install the required dependencies using the `requirements.txt` file:
```bash
pip install -r requirements.txt
```

## 💡 Notes

- **AWS Costs**: Ensure all AWS resources (Redshift cluster, S3, EC2 instances) are terminated after completing the project to avoid additional costs. 💸
- **Power BI Setup**: For Power BI, clear cached credentials if encountering login errors when connecting to Redshift. 🔐
- **Error Handling**: The DAG includes basic error handling for failed tasks; check Airflow logs for debugging. 🛠️

--- 
