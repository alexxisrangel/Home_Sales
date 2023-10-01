# Home_Sales
Big Data module challenge 

This Python script is designed to analyze home sales data using PySpark. 

Table of Contents

1. Introduction
2. Installation
3. Usage
4. Performance


## Introduction 
This script utilizes PySpark to analyze home sales data from an AWS S3 bucket. It performs operations such as calculating the average price of home based on different criteria and caching data for imporved performance. The main purpose of this code is to compare benchmarks between run times for spark temporary view, cache data and partition data.  

### Installation 

Before using this script, make sure you have the following prerequisites installed: 
- Python (>=36)
- PySpark
- Apache Spark
- findspark

#### Usage 

1. Import the necessary libraries and initialize Spark:
   ![Screenshot 2023-10-01 at 12 00 40 PM](https://github.com/alexxisrangel/Home_Sales/assets/129305054/8f406142-a7ec-4d79-81a7-976f53e1911b)

3. Read in AWS S# bucket data into a PySpark DataFrame:
   ![Screenshot 2023-10-01 at 12 01 01 PM](https://github.com/alexxisrangel/Home_Sales/assets/129305054/13eae9df-33fd-45e2-828b-73cf387ba856)
   ![Screenshot 2023-10-01 at 12 02 11 PM](https://github.com/alexxisrangel/Home_Sales/assets/129305054/ea4411ce-c423-4df1-8fac-8590b8851c2d)

5. Analyzing the data based on various criteria with Spark SQL querires. Below are some examples:
   ![Screenshot 2023-10-01 at 12 03 56![Screenshot 2023-10-01 at 12 04 13 PM](https://github.com/alexxisrangel/Home_Sales/assets/129305054/1a0130c4-27e9-4a44-9017-5393a4505682)
    PM](https://github.com/alexxisrangel/Home_Sales/assets/129305054/ce1c0275-b118-45c5-b131-d661a099c3f2)
![Screenshot 2023-10-01 at 12 04 22 PM](https://github.com/alexxisrangel/Home_Sales/assets/129305054/b5bd3d72-cae2-4e49-bc45-794e57469b3d)

7. Next, I determined the run time for one of the queries. Now there is a metric to compare with cache and parquet queries. The run time for this query was 0.1586780548095703 seconds. 

   ![Screenshot 2023-10-01 at 12 10 56 PM](https://github.com/alexxisrangel/Home_Sales/assets/129305054/8838827d-2e19-410a-9d68-476c34dd8dee)


5. Next step was to cache a temporary table titled home and of course verify if the table was cached correctly
   
    ![Screenshot 2023-10-01 at 12 12 38 PM](https://github.com/alexxisrangel/Home_Sales/assets/129305054/4b904eb5-e11d-4036-8b6d-37583607f2c9)

6. Using the cache data a new query was ran to compare to our query with no cache data. The cache query had a run time of 0.09131002426147461 seconds, which was slightly quicker than our initial benchmark
   ![Screenshot 2023-10-01 at 12 14 40 PM](https://github.com/alexxisrangel/Home_Sales/assets/129305054/35cdd019-7db7-453d-8bde-c2c9eb40fab3)

7. In order to parquet my data I first needed to partition based on "date_built" field. I proceeded to reaad in the formatted parquet data and create a temporary table
   
   ![Screenshot 2023-10-01 at 12 19 42 PM](https://github.com/alexxisrangel/Home_Sales/assets/129305054/30d9affc-76ad-47a8-90e1-c44ab2e71da5)

8. Finally for the last test we had the partision data come in at .02 seconds fasted than the cache dataset. The results don't seem drastic with this small query. However, on a larger dataset with running more complex queries, the increase in performance will be more critical. 
   ![Screenshot 2023-10-01 at 12 20 45 PM](https://github.com/alexxisrangel/Home_Sales/assets/129305054/c6a8ed76-af09-4780-9aff-7ed190138778)


##### Performance 

In conclusion, Parquet files had a better performance compared to cache data. Although in this example the differences were in milliseconds, in the long run it could potentialy save your stakeholder/client money and resources. 


   

