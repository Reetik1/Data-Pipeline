# Building an Azure Data Analytics Platform for NYC Payroll Data

##  What This Project Is About
Hey! This is my capstone project from the Udacity Data Engineering Nanodegree where I built an analytics platform for NYC payroll data. Basically, I had to take a bunch of messy CSV files with employee salary information and turn them into something useful that both city officials and regular people can understand.
The whole point was to help NYC figure out how they're spending money on salaries and overtime, and make that information available to the public. Pretty cool to work on something that actually matters for transparency in government!

##  The Problem I Was Solving
The City of New York had all this payroll data scattered around in different CSV files from various agencies, and they needed:

A way to see how much they're spending on overtime (apparently it's a lot!)
To understand which departments are costing the most money
To make all this information public so taxpayers can see where their money goes
Better reporting tools instead of manually going through spreadsheets

##  My Solution
I built an end-to-end data pipeline using Azure cloud services. Here's what it does:

Takes raw CSV files from different city agencies
Cleans up the messy data (there was a LOT of cleanup needed)
Combines everything into one clean database
Creates calculated fields like total compensation per employee
Makes it all available through Azure Synapse for analysis

##  Technology Stack

- Data Lake: Azure Data Lake Gen2 (Hierarchical Namespaces)
- Data Warehouse: Azure SQL Database
- ETL/ELT Platform: Azure Data Factory
- Analytics Engine: Azure Synapse Analytics
- Version Control: GitHub Integration
- Monitoring: Azure Data Factory Monitoring

## Data Model
-  Source Data Structure
The platform processes municipal payroll data with the following structure:
Master Data Tables

- AgencyMaster → City agency reference data
- TitleMaster → Job title classifications and pay scales
- EmpMaster → Employee master information and demographics

Transactional Data

- nycpayroll_2020 → Historical payroll transactions for 2020
- nycpayroll_2021 → Current payroll transactions for 2021

Target Analytics Schema

- Aggregated Payroll Data → Consolidated view with calculated fields:

- TotalPaid = RegularGrossPaid + TotalOTPaid + TotalOtherPay

## Project Implementation
Task 1: Azure Infrastructure Setup

- Created Azure Data Lake Gen2 with hierarchical namespace
- Provisioned Azure SQL Database for structured data warehouse
 - Configured Azure Data Factory for data integration
- Set up Azure Synapse Analytics workspace for advanced analytics
![Task 1 Copy](https://github.com/Reetik1/Data-Pipeline/blob/8b29f296e246244e243157c91bf3e4fba0fe5e99/Udacity%20Data%20Pipeline%20project/1.jpg)

![Task 2 Copy](https://github.com/Reetik1/Data-Pipeline/blob/8b29f296e246244e243157c91bf3e4fba0fe5e99/Udacity%20Data%20Pipeline%20project/2.jpg)

![Task 3 Copy](https://github.com/Reetik1/Data-Pipeline/blob/8b29f296e246244e243157c91bf3e4fba0fe5e99/Udacity%20Data%20Pipeline%20project/3.jpg)

Task 2: Linked Services Configuration

- Azure Data Lake Gen2 Connection: AzureBlobFS linked service
- Azure SQL Database Connection: AzureSQLDatabase linked service
- Established secure connections with proper authentication
- Configured connection pooling and timeout settings
![Task 3 Copy](https://github.com/Reetik1/Data-Pipeline/blob/8b29f296e246244e243157c91bf3e4fba0fe5e99/Udacity%20Data%20Pipeline%20project/1Linked%20service/4.jpg)



Task 3: Dataset Creation & Schema Mapping

- Created datasets for all source CSV files in Data Lake Gen2
- Configured AzureBlobFSLocation datasets with proper schemas
- Set up AzureSqlTable datasets for SQL Database tables
- Implemented data type mapping and validation rules

![Task 5 Copy](https://github.com/Reetik1/Data-Pipeline/blob/8b29f296e246244e243157c91bf3e4fba0fe5e99/Udacity%20Data%20Pipeline%20project/2Data%20Sets/5.jpg)


Task 4: Data Flow Development

- Master Data Flows: Mapping data from Data Lake to SQL Database
- Payroll Aggregation Flow: Union operations with derived columns
- Data Movement Flows: Staging and target data preparation
- Implemented error handling and data quality checks
![Task 7 Copy](https://github.com/Reetik1/Data-Pipeline/blob/8b29f296e246244e243157c91bf3e4fba0fe5e99/Udacity%20Data%20Pipeline%20project/3DataFlow/6.jpg)

![Task 8 Copy](https://github.com/Reetik1/Data-Pipeline/blob/8b29f296e246244e243157c91bf3e4fba0fe5e99/Udacity%20Data%20Pipeline%20project/3DataFlow/7.jpg)

Task 5: Pipeline Orchestration

- Created ExecuteDataFlow activities for data processing
- Implemented dynamic parameterization for flexible execution
- Set up pipeline triggers and scheduling mechanisms
- Configured monitoring and alerting for pipeline health

![Task 10 Copy](https://github.com/Reetik1/Data-Pipeline/blob/8b29f296e246244e243157c91bf3e4fba0fe5e99/Udacity%20Data%20Pipeline%20project/4Pipelines/8.jpg)


Task 6: Data Transformation & Aggregation

- Developed comprehensive payroll calculation logic
- Implemented TotalPaid calculation: RegularGrossPaid + TotalOTPaid + TotalOtherPay
- Created aggregated views for analytical reporting
- Optimized data flows for performance and scalability
![Task 11 Copy](https://github.com/Reetik1/Data-Pipeline/blob/8b29f296e246244e243157c91bf3e4fba0fe5e99/Udacity%20Data%20Pipeline%20project/4Pipelines/9.jpg)

Task 7: Synapse Analytics Integration

- Built external tables in Synapse Analytics
- Connected to Data Lake staging directory
- Implemented analytical queries for public reporting
- Created views for dashboard and reporting tools
![Task 10 Copy](https://github.com/Reetik1/Data-Pipeline/blob/8b29f296e246244e243157c91bf3e4fba0fe5e99/Udacity%20Data%20Pipeline%20project/5Data%20Verification/10.jpg)
![Task 11 Copy](https://github.com/Reetik1/Data-Pipeline/blob/8b29f296e246244e243157c91bf3e4fba0fe5e99/Udacity%20Data%20Pipeline%20project/5Data%20Verification/11.jpg)
![Task 12 Copy](https://github.com/Reetik1/Data-Pipeline/blob/8b29f296e246244e243157c91bf3e4fba0fe5e99/Udacity%20Data%20Pipeline%20project/5Data%20Verification/12.jpg)
## ETL Pipeline Features

- Dynamic Pipelines: Parameterized for flexible data processing
- Union Operations: Combining multiple data sources efficiently
- Derived Columns: Calculated fields for business metrics
- Error Handling: Comprehensive error detection and recovery
- Monitoring: Real-time pipeline execution tracking
- Scalability: Handles large-volume municipal data processing

## Data Quality & Validation

- Verified data completeness in Azure Data Lake Gen2
- Monitored successful data loading into SQL Database
- Validated aggregation calculations and business rules
- Tested Synapse Analytics external table queries
- Implemented automated data quality checks


## Key Achievements

Scalable Architecture: Handles multi-gigabyte municipal datasets efficiently
Public Transparency: Enables citizen access to budget allocation data
Cost Optimization: Serverless and pay-per-use Azure services
Data Integration: Seamless flow from raw data to analytics-ready format
Automation: Fully automated ETL with minimal manual intervention
Quality Assurance: Comprehensive testing and validation processes

## 📊 Business Impact
This data analytics platform enables the City of New York to:

Budget Transparency: Provide public access to salary and overtime spending
Financial Analysis: Identify trends in overtime allocation across agencies
Resource Optimization: Make data-driven decisions on staffing and budgets
Public Accountability: Demonstrate responsible use of taxpayer resources
Operational Efficiency: Automate manual reporting processes
