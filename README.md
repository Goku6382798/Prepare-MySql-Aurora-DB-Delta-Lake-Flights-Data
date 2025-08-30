# Prepare MySQL Aurora DB | Delta Lake | Flights Data

This project demonstrates how to prepare and process flight datasets using **MySQL Aurora DB** for storage, **PySpark** for ETL, and **Delta Lake** on Amazon S3 for scalable analytics.  

---

## 📊 Architecture
![Architecture](architecture/Screenshot%20from%202025-08-30%2014-51-27.png)

---

## 📂 Project Structure

Prepare MySql Aurora DB | Delta Lake | Flights Data
│

├── architecture

│   ├── glue_pyspark.pdf                  # Detailed project documentation

│   └── Screenshot...png                  # Architecture diagram

│

├── flights-data

│   ├── flight_logistics.csv              # Logistics dataset

│   ├── flights.csv                       # Flight details dataset

│   └── passenger_experience.csv          # Passenger experience dataset

│

└── mysql-queries.sql                     # SQL queries for Aurora DB setup

---

## ⚙️ Tech Stack
- **Amazon Aurora MySQL** – Source database  
- **PySpark (AWS Glue)** – ETL processing  
- **Amazon S3** – Data lake storage  
- **Delta Lake** – Transactional storage layer on S3  

---

## 🚀 Steps to Create a Delta Lake inside Amazon S3

1. **Prepare MySQL Aurora DB**
   - Run the queries in `mysql-queries.sql` to create schema and load flight data.

2. **Extract Data using AWS Glue / PySpark**
   - Create a Glue job (or Spark job) to extract data from Aurora into DataFrames.

   ```python
   df_flights = spark.read \
       .format("jdbc") \
       .option("url", "jdbc:mysql://<aurora-endpoint>:3306/<db_name>") \
       .option("user", "<username>") \
       .option("password", "<password>") \
       .option("dbtable", "flights") \
       .load()

