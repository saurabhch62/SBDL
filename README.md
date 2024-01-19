# SBDL - Spark Bulk Data Load Application
Developing a Data Pipline for a Bank which takes the raw data from sources, process and prepare it according to the given requirement and send it to the Kafka cluster for Consumtion.

The bank has a master data management platform.This platform is basically a central data management platform.This platform is designed to synchronize master data within applications across the enterprise. It is critical to managing data that accurately represents business entities such as clients, employees, products, and facilities. We will bring data from this platform to Kafka once every day.

Source Could be anything like kafka stream, files or Database, our aim is to take the data in CSV or parquet format from the source. 

Tech Stack Requirement :
1. Hadoop Cluster
2. PySpark
3. Hive
4. YARN
5. Jenkins (optional for this project)
6. Github (for maintaing the source code)

Load Type : Full load every day and maintaing 7 days of records.

Flow of the Project :
1. Read the data from the Hive Table
2. Transform it according to the requirements
3. And, send it to Kafka in the JSON format (key-value).
   
Assumption :
1. We already have a data ingestion pipeline in place.
2. Data from source is being ingested into Hive tables.


Key Things to Note :
1.Lot of systems connecting to the MDM platform and copying data from MDM will put a lot of workload on the MDM. This approach is not scalable. So how do we design it? We decided to put a Kafka system in between these two ends. Once you have Kafka, we will bring entity data from MDM to Kafka. Then let these systems read from Kafka. This arrangement will make our system scalable without too much load on the MDM platform. We will bring data from MDM to Kafka once every day.
