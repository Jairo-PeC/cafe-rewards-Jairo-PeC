# cafe-rewards-Jairo-PeC
Cafe reward offers challenge

# AWS Data Lake(House) Architecture for Cafe reward offers

**Author**: Jairo Enrique Peña Cruz  
**Date**: March 3, 2025  
**GitHub**: [https://github.com/Jairo-PeC]  
**Email**: [jairopecruz@gmail.com]  

## Overview
This project outlines a data lake architecture built on AWS, designed to ingest, process, and analyze data from various sources through a multi-layered approach using star schema method (Kimball): Raw, Trusted, Enriched, and Consumption. The architecture leverages AWS services like Amazon S3, AWS Glue, AWS Lake Formation, Amazon Redshift, Amazon Athena, and Amazon QuickSight to create a scalable, secure, and efficient data pipeline.

## Architecture Diagram
![Cafe rewards offers - Ballastlane challenge - Jairo Peña drawio](https://github.com/user-attachments/assets/aaf5c5a3-3cb4-4428-960e-572edce2eedf)

### Data Flow
1. **Sources → Raw Layer**: Data from APIs is ingested into "Raw Data (S3)" using AWS Glue and Amazon API Gateway.
2. **Raw → Trusted Layer**: Glue ETL jobs clean, transform and standarize raw data into Parquet files in "Trusted Data (S3)", with AWS Lake Formation providing governance.
3. **Trusted → Enriched Layer**: Data is either enriched into Parquet files too, in "Enriched Data (S3)" via Glue or loaded into Amazon Redshift for structured analytics. Amazon Athena queries S3 directly for ad-hoc queries.
4. **Enriched → Consumption**: BI tools like Amazon QuickSight consume enriched data via Athena or Redshift. Athena is also a place to experiment with enriched datasets. External BI tools (Power BI, Tableau, etc.) can be used at will if needed.

## Design Choices and Technologies
- **Sources to Raw (S3)**:
  - **AWS Glue**: Serverless ETL for ingestion and metadata discovery.
  - **Amazon API Gateway**: Secure API ingestion.
  - **Amazon S3**: Cost-effective, scalable raw storage.

- **Raw to Trusted (S3)**:
  - **AWS Glue**: Cleans and transforms data.
  - **AWS Lake Formation**: Centralizes metadata and access control.
  - **Amazon S3 (Parquet)**: Trusted storage with standardized data and formats.

- **Trusted to Enriched**:
  - **AWS Glue**: Converts to Parquet or loads into Redshift.
  - **Amazon S3 (Parquet)**: Optimized for analytics.
  - **Amazon Redshift**: High-performance data warehouse where datamarts can be placed if needed. Can be expensive.
  - **Amazon Athena**: Serverless querying of S3 data.

- **Consumption**:
  - **Amazon QuickSight**: BI for dashboards and insights.
  - **Choice**: Balances flexibility (Athena) and performance (Redshift).

## Analytical Questions Answered
1. **Channel Effectiveness**: Web channel leads with a 51.03% offer completion rate.
2. **Age Distribution**: 41-60 age group has the highest completion rate (82.29%).
3. **Time to Complete**: The average time to complete an offer is 52.59 hours.

## Setup Instructions
- **Run it from**:[https://colab.research.google.com/github/Jairo-PeC/cafe-rewards-Jairo-PeC/blob/main/Ballastlane_Data_Engineer_exercise_Jairo_Pe%C3%B1a.ipynb]
- **Git clone** [(https://github.com/Jairo-PeC/cafe-rewards-Jairo-PeC.git)]

## Note
All code in this repository was executed in Google Colab as a simulation/mock-up to demonstrate the data processing logic. The architecture described above represents the intended design using AWS services, which would be implemented in a production environment as outlined.
