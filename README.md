# AWS-ETL-Pipeline-using-Python-on-Youtube-Data 
build ETL Data Pipeline in Python on YouTube Data using Athena, Glue and Lambda.
Over 2.6 billion individuals worldwide use YouTube monthly, making it one of the top-most visited websites
# ETL Process for "Build an AWS ETL Data Pipeline in Python on YouTube Data"

## Architecture Diagram Overview
- **Data Source**: YouTube data in JSON format is ingested.
- **Amazon S3**: Acts as the data lake, storing raw JSON files.
- **AWS Glue**: Crawlers and jobs are used for schema detection and data transformation.
- **AWS Lambda**: Functions handle the conversion of JSON data to Parquet format.
- **Amazon Athena**: Provides SQL querying capabilities for the data stored in S3.
- **AWS QuickSight**: Used for creating visualizations and dashboards on the processed data.

## Detailed ETL Steps

### 1. Project Overview and Setup
   - Understand the project scope and goals.
   - Create a new AWS user with appropriate permissions to access S3, Glue, Lambda, and other services.
   - Set up AWS CLI for interacting with AWS services programmatically.

### 2. Extract Phase
   - **Data Ingestion**: Store YouTube data in JSON format within an Amazon S3 bucket.
   - **AWS Glue Crawler**: Create a crawler to detect the schema of the raw JSON files in S3 and catalog the metadata.

### 3. Transform Phase
   - **JSON to Parquet Conversion**: Using AWS Lambda, the data is transformed from JSON format to the more efficient Parquet format:
     - The process is broken into multiple steps for clarity, where Lambda functions are tested and configured.
     - AWS Data Wrangler is integrated as a layer to simplify working with data in AWS.
   - **AWS Glue Spark Job**: Configured to perform additional transformations like filtering, aggregating, and optimizing the data.
     - Explore the generated code and configure pushdown predicates for efficient data processing.
     - Modify schema data types if needed to ensure data integrity.
   - **Materialization**: Store the transformed Parquet data back into an S3 bucket for efficient querying.

### 4. Load Phase
   - **Data Storage**: The transformed Parquet files are stored in the S3 bucket, organized for analysis.
   - **Athena Setup**: Configure Athena to point to the result location in S3 and run SQL queries to explore and analyze the transformed data.
   - **Visualization**: Use AWS QuickSight to create dashboards and visualizations based on the data processed by Athena.

### 5. Automation and Optimization
   - **Triggers and Scheduling**: Add triggers to AWS Lambda functions and automate Glue jobs using AWS Glue Studio for ongoing data processing.
   - **Automate Glue Job**: Set up schedules and triggers to ensure that data is processed automatically as new YouTube data becomes available.
   - **Review and Recap**: Periodically recap the architecture and ensure that the data pipeline is running smoothly.

### 6. Historical Data Exploration
   - Query historical data using Athena to understand trends over time.
   - Update and refine table schemas based on new insights or changes in the dataset.

This ETL process ensures that raw YouTube data is efficiently extracted, transformed, and loaded into a structured format suitable for analysis. By leveraging AWS tools like Glue, Lambda, and Athena, it allows for scalability and adaptability as data volumes and analysis needs grow.
