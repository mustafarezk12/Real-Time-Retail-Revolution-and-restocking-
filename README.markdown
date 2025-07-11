# Real-Time Retail Revolution: Pioneering a Scalable IoT Data Pipeline for Inventory Optimization
![Architecture](arch.svg)
## Architecture Overview
This project features a robust real-time data pipeline designed for a multi-branch retail environment. The architecture includes:
- **Apache Kafka with KRaft** on AWS EC2: Central message streaming platform handling ~10-50 messages/second.
- **AWS Lambda**: Serverless processing for validation, transformation, and routing.
- **Amazon SQS**: Queue for buffering and Dead Letter Queue (DLQ) for invalid data audit.
- **Amazon OpenSearch Service**: Real-time indexing and search for analytics.
- **Amazon Redshift**: Data warehouse for large-scale querying.
- **Amazon S3**: Storage for raw and processed data (e.g., CSV for Redshift).
- **Visualization**: OpenSearch Dashboards and QuickSight for insights.

Data flows from IoT sources (shelf sensors, warehouse systems, POS, external data) to Kafka, processed by Lambda, and routed to OpenSearch, S3, and Redshift.

## Project Summary
This in-progress initiative develops a scalable IoT data pipeline to optimize inventory management for an online retail store. It ingests real-time data from four sources, validates and transforms it using cloud-native AWS services, and enables efficient analytics. The project leverages Python for data generation, ensuring a test dataset of 1,000 mixed valid/invalid records to simulate retail operations.

## Key Features
- Real-time processing of shelf stock, sales, warehouse inventory, and external data.
- Automated pipeline with Kafka for ingestion, Lambda for processing, and S3/Redshift for storage.
- OpenSearch integration for instant search and visualization.
- Data governance with SQS DLQ for invalid record auditing.
- AWS Free Tier compatibility for cost-effective development.

## Setup Instructions
1. **Prerequisites**: AWS account, EC2 instance, Python 3, Faker library (`pip install faker`).
2. **Deploy Kafka**: Install Kafka with KRaft on EC2, create `retail_data` topic.
3. **Generate Data**: Run `generate_fake_mixed_data.py` to create `fake_mixed_data.json` with 1,000 records.
4. **Ingest Data**: Use a producer to send records to Kafka’s `retail_data` topic.
5. **Configure Lambda**: Set up `RetailDataProcessor` with Kafka event source, S3, SQS, and OpenSearch permissions.
6. **Test**: Send 100 records, verify data in OpenSearch, S3, and DLQ.

## Next Steps
- Optimize Lambda batch processing for higher throughput.
- Enhance Redshift schema with additional dimensions (e.g., Branch_Dim, Product_Dim).
- Integrate live IoT data sources.
- Expand visualization with QuickSight dashboards.

## Contributing
This is a personal project in progress. Suggestions for scalability or AWS optimization are welcome via GitHub issues.

## License
MIT License (or specify your preference).
