# WD-AWS-SF
Weather Data Ingestion Pipeline

This project implements a data ingestion pipeline to fetch weather data from a Weather API, process it using AWS services, and load it into Snowflake for analysis.

Overview

The pipeline architecture includes the following components:





Weather API: Provides real-time weather data.



AWS Lambda: Scheduled to load data from the Weather API.



DynamoDB: Stores the ingested weather data with a stream enabled.



AWS Lambda (Stream Processor): Processes DynamoDB stream data and loads it into an S3 bucket.



Snowflake: Final destination for data storage and analysis, integrated via STS (Secure Token Service).



S3: Acts as an intermediary storage for streaming data before loading into Snowflake.


Setup Instructions

Prerequisites





AWS account with permissions to create Lambda functions, DynamoDB tables, and S3 buckets.



Snowflake account with appropriate roles and permissions.



AWS CLI and Snowflake CLI configured.



Python (for Lambda functions and scripts).

Files


Fetch_Weather_data.py: Python script to fetch weather data from the Weather API.


Ddb-stream-s3.py: Python script to process DynamoDB streams and load data into an S3 bucket.




snowflake.sql: SQL script to create the Snowflake database, table, stage, and pipe for data ingestion.

Steps





Set up AWS Resources:





Deploy Fetch_Weather_data.py as a Lambda function with a scheduled trigger (e.g., cron schedule).



Configure a DynamoDB table to store weather data with stream enabled.



Deploy Ddb-stream-s3.py as a Lambda function to process DynamoDB streams and write to an S3 bucket.



Create an S3 bucket to store the streamed data.



Configure Snowflake:





Execute snowflake.sql in your Snowflake environment to set up the database, table, storage integration, stage, and pipe.



Deploy the Pipeline:





Deploy the Lambda functions using AWS CLI or a deployment tool (e.g., Serverless Framework).



Test the end-to-end flow by triggering the Fetch_Weather_data.py Lambda function manually.



Monitor and Maintain:





Check Snowflake tables for ingested data.



Monitor Lambda logs and DynamoDB streams for errors.

File Structure





lambda/: Contains Ddb-stream-s3.py and Fetch_Weather_data.py.



snowflake/: Contains snowflake.sql.


Usage





Schedule the Fetch_Weather_data.py Lambda function to run at desired intervals.



Query the Snowflake table to analyze weather data.

Contributing

Feel free to submit issues or pull requests. Please include detailed descriptions of changes.
