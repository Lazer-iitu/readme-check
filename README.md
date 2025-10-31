# SIS End-to-End Data Pipeline Project
This project demonstrates a data engineering pipeline built using **HDFS, Apache Spark, Parquet, and Kafka**.

## Pipeline:
XLSX -> CSV -> HDFS -> PySpark ETL -> Parquet partitioned by Country -> Kafka Producer -> Kafka Consumer

## Files
- **SIS1_Lazer.ipynb** : PySpark job to clean, compute TotalAmount and monthly revenue, writes Parquet/CSV
- **kafka_producer.py** : reads aggregated data and publishes each row as JSON to Kafka
- **kafka_consumer.py** : consumes topic and prints messages

## Architecture
1. Data Source
The raw dataset (`online_retail_II.csv`) is stored in **HDFS** under `/sis_project`.

2. Spark Processing
Apache Spark reads the CSV data from HDFS and performs cleaning, aggregation, and transformation.After writes the processed output in **Parquet format** back to HDFS.

3. Parquet Storage
Parquet files provide efficient columnar storage and compression for analytics.

4. Kafka Streaming
The final aggregated or filtered results are sent to a **Kafka topic (`daily_revenue`)**, making the data available for real-time streaming or downstream systems.

## Technologies Used
- **Apache Hadoop (HDFS)** -distributed storage  
- **Apache Spark** - ETL and data processing  
- **Apache Kafka** - real-time data streaming  
- **Docker Compose**- containerized environment setup  

### 📂 HDFS Structure
```
/sis_project
│── online_retail_II.csv
│── sales_parquet/
│── sales_csv/
```
