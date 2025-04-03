# 🎵 Spotify Data Pipeline using AWS & Snowflake

## Project Overview
This project involves implementing an ETL pipeline that integrates Spotify API, AWS, and Snowflake. The pipeline extracts music data (albums, artists, and tracks) from the Spotify API, processes it using AWS Glue (Spark), and stores the transformed data in Amazon S3. Finally, the data is ingested into Snowflake for structured analysis and reporting.

## Architecture
![Architecture Diagram](Diagram.png)

## Key Components
### Data Extraction
- **Spotify API:**  Retrieve music data, including track details, artist information, and albums.
- **AWS Lambda:** Fetches raw JSON data from the API and stores it in Amazon S3.
- **Amazon CloudWatch:** Automates and schedules the extraction process.

### Data Transformation
