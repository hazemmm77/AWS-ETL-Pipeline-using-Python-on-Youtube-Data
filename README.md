# AWS-ETL-Pipeline-using-Python-on-Youtube-Data (Data Lake)
build ETL Data Pipeline in Python on YouTube Data using Athena, Glue and Lambda.
Over 2.6 billion individuals worldwide use YouTube monthly, making it one of the top-most visited websites
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
 ## How To Run the Project
 * Useing aws CLI upload files to s3 (landing area)(commands in Amazon S3 CLI copy commands file)
 * Add a trigger for the Lambda function, such as an S3 upload event
 * lambda function detect new files upload and convert json and csv file to s3(Cleansed/Enriched area) as parquet files partitioned and compressed
 * Using glue job join two tables (using athina) and save in reporting area as parqeut file 
 * Use Glue crawler to create data catalog(database) for every area (landing area,Cleansed/Enriched area,Reporting area)
 * Using Athina you can access (Cleansed/Enriched,Reproting area) s3 for BI solutions like Quicksite .
 * You can use AWS CloudWatch Events for scheduling.
 * You can use AWS CloudWatch to monitor pipline
 * Monitor the Glue job logs for errors and successful completion.
   
### Project  files
 1. ```Amazon S3 CLI copy commands``` CLI commnds to Upload youtupe files to S3.
 2. ```lambda function``` to convert json file to parquet and save it in s3 .
 3.  ```Spark code Glue job``` to clean and wrangelr files before savedSpark code Glue job in s3.
 4.  ```Architecture.jpg ``` the Architecture of the project
 5. ```README.md``` provides discussion on your project.
