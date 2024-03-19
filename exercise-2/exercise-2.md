# Exercise 2 - Transform data using notebooks and Spark clusters 

Timebox: 75 minutes
> Back to [Agenda](./../README.md#agenda)


# Context


%TODO STORY


1. Create a notebook
2. Load data from Lakehouse tables into Spark DataFrames
3. Spark vs Pandas
3. Transform the data using Spark SQL and PySpark APIs
4. Write the transformed data back to Lakehouse tables and other storage formats (parquet)
5. Visualize and interact with the data using charts and widgets 
6. Save, schedule and run the notebook as a job 
7. WS-level settings overview 
8. Compute Settings
8. Creation of Environment
9. Git 




**The foundation of Microsoft Fabric is a Lakehouse**, which is built on top of the **OneLake** scalable storage layer and uses **Apache Spark** and **SQL** compute engines for big data processing. A Lakehouse is a unified platform that combines:
- The flexible and scalable storage of a data lake
- The ability to query and analyze data of a data warehouse

Some benefits of a lakehouse include:
- Lakehouses use Spark and SQL engines to process large-scale data and support machine learning or predictive modeling analytics.
- Lakehouse data is organized in a schema-on-read format, which means you define the schema as needed rather than having a predefined schema.
- Lakehouses support ACID (Atomicity, Consistency, Isolation, Durability) transactions through Delta Lake formatted tables for data consistency and integrity.
- Lakehouses are a single location for data engineers, data scientists, and data analysts to access and use data.

A Lakehouse is a great option if you want a scalable analytics solution that maintains data consistency.

Imagine your company has been storing structured data from NYC Taxi's transactional system, such as trip history, passenger counts, and fare information in a data warehouse. However, you have also collected unstructured data from social media, website logs, and third-party sources related to NYC Taxi, which are difficult to manage and analyze using the existing data warehouse infrastructure.

Your company's new directive is to improve its decision-making capabilities by analyzing data in various formats across multiple sources. Therefore, the company decides to **leverage Microsoft Fabric's capabilities to analyze and manage these diverse datasets more efficiently**.


## Data ingestion into lakehouse
Easily ingest data into the lakehouse through a variety of methods

* Get files from your computer using direct upload
* Connect to 120+ data sources and apply multiple transformations using Dataflows or copy petabyte-sized lakes using the copy activity in Pipelines
* Use Spark code to connect to data sources using available Spark libraries
* Leverage shortcuts to create pointers to existing data in OneLake and external storage accounts with no data movement at all
* Shortcuts behave in the same way as hosted storage

Let's load the data into the lakehouse!

Now, please follow along with the instructor.




## Create lakehouse and load the data

1. Click "Add" to add lakehouse.

2. Select "New lakehouse" and click "Add".

3. Type the name "Bronze", and click "Add".

4. Download the file to your local machine: https://github.com/ekote/azure-architect/raw/master/part-00175-tid-4753095944193949832-fee7e113-666d-4114-9fcb-bcd3046479f3-2745-1.c000.parquet

5. Go to OneLake data hub > your Lakehouse

6. Upload the file

7. Use "Load to Table" feature


## The lakehouse is attached to your notebook. It's time to discover the lakehouse artifact!



The most common way to work with data in delta tables in Spark is to use Spark SQL. You can embed SQL statements in other languages (such as PySpark or Scala) by using the spark.sql library.


 

## Task 1
### Objective
### Definition of done


## Task 2
### Objective
### Definition of done



# Definition of done (and you can go to the next exercise)

> [!IMPORTANT]
> Once completed, go to [Exercise 3](./exercise-3/exercise-3.md) or continue with [Advanced steps below](#advanced-steps).


# Advanced steps