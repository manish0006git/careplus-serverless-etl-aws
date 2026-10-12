# CarePlus Serverless Data Platform on AWS

A serverless ETL pipeline built using AWS to ingest healthcare support tickets and support logs, transform raw data into structured datasets, and make it available for SQL analytics and dashboards. The project uses AWS Lambda for data processing, Amazon S3 for storage, Amazon Athena for querying data in S3, and Amazon Redshift for data warehousing and analytical queries.

**Tech Stack:** Python · SQL · Amazon S3 · AWS Lambda · AWS Glue · Amazon Athena · Amazon Redshift · IAM

---

## 📌 Overview

This project demonstrates a cloud-based data engineering workflow using serverless AWS services:

1. **Extract** support tickets and support logs from the CarePlus source system.
2. **Store** incoming data in Amazon S3 for raw data retention.
3. **Transform** raw data using AWS Lambda into structured, analysis-ready datasets.
4. **Catalog** datasets using AWS Glue for discovery and analytical access.
5. **Analyze** data using Amazon Athena to query datasets directly from S3.
6. **Load** processed data into Amazon Redshift for data warehousing and SQL analytics.
7. **Visualize** analytical results through a dashboard.

## 🏗️ Architecture

![Pipeline Architecture](architecture/pipeline-architecture.svg)

```text
CarePlus Source System
          |
          v
   AWS Lambda
    Ingestion
          |
          v
   Amazon S3 (Raw)
          |
          v
   AWS Lambda
  Transformation
          |
          v
 Amazon S3 (Processed)
          |
          +--------------------+
          |                    |
          v                    v
   Amazon Athena        Amazon Redshift
   SQL on S3            Data Warehouse
          |                    |
          +---------+----------+
                    |
                    v
             SQL Analytics
              & Dashboard
```

AWS Glue supports data cataloging and integration with the analytical services.

## 📂 Project Structure

```text
CarePlus-Serverless-Data-Platform/
├── data-ingestion/              # Ingest support tickets and logs
├── data-transformation/         # Clean and transform raw data
├── data-warehousing-analytics/  # Redshift loading and SQL queries
├── database/                    # Source schema and sample data
├── dashboard/                   # Dashboard and screenshots
├── architecture/                # Pipeline architecture diagram
├── iam/                         # IAM policy JSON files
├── sample-data/                 # Sample datasets
└── README.md
```

## ⚙️ AWS Services

| Service             | Purpose                                                     |
| ------------------- | ----------------------------------------------------------- |
| **Amazon S3**       | Stores raw and processed datasets.                          |
| **AWS Lambda**      | Executes serverless ingestion and transformation logic.     |
| **AWS Glue**        | Supports data cataloging and data integration.              |
| **Amazon Athena**   | Runs SQL queries directly against supported datasets in S3. |
| **Amazon Redshift** | Stores data in warehouse tables for analytical SQL queries. |
| **AWS IAM**         | Manages permissions and secure access between AWS services. |
| **Python & SQL**    | Handle data processing and analytical queries.              |

## 🔍 Athena vs. Redshift

Both services support SQL analytics but serve different purposes in this project.

* **Amazon Athena:** Used to query data stored in Amazon S3 without first loading it into Redshift. Useful for ad-hoc analysis and exploring processed datasets.
* **Amazon Redshift:** Used as the data warehouse for storing processed data in tables and performing structured analytical queries.

Using both services demonstrates how S3-based analytics and data warehousing can complement each other in a cloud data platform.

## 📊 Analytics and Dashboard

The processed data can be analyzed using SQL to explore support ticket volumes, ticket categories, ticket statuses, and patterns in support activity, depending on the available data.

The dashboard presents analytical results in a visual format, making it easier to understand the information than by examining raw datasets alone.

![Dashboard Preview]/(data-warehousing-analytics/dashboard/Careplus Insights.pbix>)



## 🚀 Setup and Execution

1. Create the required Amazon S3 buckets for raw and processed data.
2. Configure IAM roles and permissions for the AWS services.
3. Deploy the ingestion and transformation Lambda functions.
4. Configure AWS Glue and Athena to access the processed datasets.
5. Set up Amazon Redshift and load the processed data into warehouse tables.
6. Execute SQL queries in Athena and Redshift to validate and analyze the data.
7. Connect the analytical results to the dashboard.

**Prerequisites:** An AWS account with the required service permissions, Python for development, and the configuration needed by the pipeline.

## 🔧 Challenges and Learnings

* Working with IAM roles and permissions for AWS service access.
* Separating raw and processed data using Amazon S3.
* Implementing serverless data processing with AWS Lambda.
* Understanding the difference between querying data in S3 with Athena and using Redshift as a data warehouse.
* Preparing structured datasets for SQL analytics and dashboard reporting.


## 👤 Author

**Manish Bawa** — B.E. Computer Engineering | Aspiring Data Engineer

A hands-on AWS project exploring serverless ETL pipelines, cloud data storage, SQL analytics, and data warehousing.
