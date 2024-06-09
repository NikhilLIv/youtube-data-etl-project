# YouTube Data ETL Project

This repository contains the code and documentation for an ETL (Extract, Transform, Load) project that processes YouTube data. The project leverages various AWS services including S3, Glue, Lambda, Athena, IAM, CloudWatch, and QuickSight. The source data comprises video-level information in CSV format and video category information in JSON format, both sourced from Kaggle.

## Project Overview

The project follows these major steps:

1. **Data Ingestion**: Upload raw data (CSV and JSON files) to S3.
2. **Data Cleaning**: Use AWS Glue and Lambda to clean the raw data and store the cleaned data in another S3 bucket.
3. **Data Transformation**: Join the cleaned video-level and category-level data using AWS Glue and store the result as a Parquet file in an analytics S3 bucket.
4. **Data Analysis**: Create a minimalistic dashboard in AWS QuickSight using the Parquet file.

## Architecture Diagram

![architecture](https://github.com/NikhilLIv/youtube-data-etl-project/assets/63955237/5854193a-5669-4e5b-850e-d617db41e69c)


## AWS Services Used

- **Amazon S3**: For storing raw, cleaned, and transformed data.
- **AWS Glue**: For cleaning, transforming, and joining the data.
- **AWS Lambda**: For triggering Glue jobs and additional data processing.
- **Amazon Athena**: For querying data directly from S3.
- **AWS IAM**: For managing access and permissions to AWS resources.
- **Amazon CloudWatch**: For logging and monitoring.
- **Amazon QuickSight**: For data visualization and dashboard creation.

## Data Sources

- **Video-level data**: CSV file from Kaggle containing details about individual YouTube videos.
- **Video category data**: JSON file from Kaggle containing information about video categories.

## Project Steps

### 1. Data Ingestion

- Upload the raw CSV and JSON files to an S3 bucket (`s3://raw-bucket`).

### 2. Data Cleaning

- **AWS Glue**: 
  - Create Glue jobs to clean the CSV and JSON files.
  - Convert the cleaned data to a common format and store it in a cleaned S3 bucket (`s3://cleaned-bucket`).

- **AWS Lambda**:
  - Trigger Glue jobs to ensure timely execution.
  - Perform any additional data processing tasks.

### 3. Data Transformation

- **AWS Glue**:
  - Join the cleaned video-level data and video category data.
  - Convert the joined data into a Parquet file format.
  - Store the transformed data in an analytics S3 bucket (`s3://analytics-bucket`).

### 4. Data Analysis

- **AWS QuickSight**:
  - Import the Parquet file from the analytics S3 bucket.
  - Create a minimalistic dashboard to visualize key metrics and insights.

## Quick Start

### Prerequisites

- AWS account with appropriate permissions for S3, Glue, Lambda, Athena, IAM, CloudWatch, and QuickSight.
- Kaggle account to download the source data.

### Steps

1. Clone this repository:
    ```bash
    git clone https://github.com/NikhilLIv/youtube-data-etl-project.git
    cd youtube-data-etl-project
    ```

2. Upload the raw data to S3:
    - Place your CSV and JSON files in the `s3://raw-bucket`.

3. Set up AWS Glue:
    - Create Glue jobs for data cleaning and transformation as per the scripts in the `glue-scripts` directory.

4. Set up AWS Lambda:
    - Create Lambda functions to trigger Glue jobs. Refer to the `lambda-functions` directory for sample code.

5. Configure IAM roles and policies:
    - Ensure all services have the necessary permissions as per the IAM configurations in the `iam-policies` directory.

6. Monitor the processes:
    - Use CloudWatch to monitor logs and performance metrics.

7. Analyze the data:
    - Use QuickSight to create your dashboard from the Parquet file stored in the `s3://analytics-bucket`.

## Repository Structure

```
youtube-data-etl/
├── glue-scripts/
│   ├── clean_video_data.py
│   ├── clean_category_data.py
│   ├── join_data.py
├── lambda-functions/
│   ├── trigger_glue_jobs.py
├── iam-policies/
│   ├── glue_policy.json
│   ├── lambda_policy.json
│   ├── s3_policy.json
├── quicksight/
│   ├── dashboard_setup_guide.md
├── README.md
└── architecture-diagram.png
```

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any changes or enhancements.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgements

- Kaggle for providing the data sets.
- AWS for the cloud infrastructure services.

---

Feel free to customize this README file further as per your project's specific details and requirements.
