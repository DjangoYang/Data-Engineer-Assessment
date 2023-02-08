# Data-Engineer-Assessment
Schema:
CREATE TABLE stock_data (
  id SERIAL PRIMARY KEY,
  stock_name VARCHAR(10) NOT NULL,
  date DATE NOT NULL,
  high FLOAT NOT NULL,
  low FLOAT NOT NULL,
  volume INTEGER NOT NULL
);

Calculation:
WEEKLY AVERAGE:
SELECT 
  stock_name, 
  date_trunc('week', date) AS week, 
  AVG(high) AS avg_high, 
  AVG(low) AS avg_low, 
  AVG(volume) AS avg_volume
FROM stock_data
GROUP BY stock_name, week;

MONTHLY AVERAGE:
SELECT 
  stock_name, 
  date_trunc('month', date) AS month, 
  AVG(high) AS avg_high, 
  AVG(low) AS avg_low, 
  AVG(volume) AS avg_volume
FROM stock_data
GROUP BY stock_name, month;

QUARTERLY AVERAGE:
SELECT 
  stock_name, 
  date_trunc('quarter', date) AS quarter, 
  AVG(high) AS avg_high, 
  AVG(low) AS avg_low, 
  AVG(volume) AS avg_volume
FROM stock_data
GROUP BY stock_name, quarter;

YEARLY AVERAGE:
SELECT 
  stock_name, 
  date_trunc('year', date) AS year, 
  AVG(high) AS avg_high, 
  AVG(low) AS avg_low, 
  AVG(volume) AS avg_volume
FROM stock_data
GROUP BY stock_name, year;

System Design:
Architecture:
The streaming pipeline can be designed as follows:

Data collection layer: In this layer, data will be collected from multiple sources, such as APIs, CSV files, etc.
Data processing layer: In this layer, data will be processed in real-time. It will calculate the rolling average of trading data for each stock for the past 20 days, 50 days, and 200 days.
Data storage layer: In this layer, the processed data will be stored in a database such as PostgreSQL.
API layer: In this layer, the processed data will be accessible through APIs.
Technologies:

Data collection layer: Apache Kafka
Data processing layer: Apache Spark Streaming
Data storage layer: PostgreSQL
API layer: Flask (Python)

Justification:

Apache Kafka: Apache Kafka is an open-source, distributed, high-throughput, and low-latency platform for handling real-time data streams. It can handle large amounts of data efficiently, making it an ideal choice for data collection.
Apache Spark Streaming: Apache Spark Streaming is a real-time data processing framework that can process high-volume data streams efficiently. It is easy to integrate with Apache Kafka and can process data in real-time.
PostgreSQL: PostgreSQL is a powerful and open-source relational database management system that is widely used for its stability, reliability, and scalability. It is suitable for storing large amounts of structured data.
Flask: Flask is a lightweight Python framework for building
