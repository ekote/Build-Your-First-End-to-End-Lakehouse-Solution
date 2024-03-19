# Exercise 2 - Transform data using notebooks and Spark clusters 

Timebox: 75 minutes
> Back to [Agenda](./../README.md#agenda)

# Context
%TODO STORY


# Task 2.1 Create a notebook




# Task 2.2 Get data from the lakehouse

To execute the cell code, use the shortcut CTRL + Enter on Windows, or ⌘ + Enter on MacOS. Alternatively, you can click the 'Run' icon (▶️) located on the left side of the code cell.

`df = spark.sql("SELECT * FROM Bronze.NYC_Taxi LIMIT 1000")` - This line of code uses the `spark.sql()` function to run an SQL query on a table called `NYC_Taxi` located in the lakehouse `Bronze`. The query selects all columns `(*)` from the table and limits the result to the first 1000 rows with the `LIMIT 1000` clause. The result of the query is then stored in a PySpark DataFrame called `df`.
`display(df)` - the `display()` function is used to visualize the contents of a DataFrame in a tabular format. In this case, it visualizes the contents of the df DataFrame created in the previous line.

```pyspark
df = spark.sql("SELECT * FROM Bronze.nyc_taxi LIMIT 1000")
display(df)
```
Alternatively, you can use the %%sql magic in a notebook to run SQL statements.

```
%%sql
SELECT * FROM Bronze.nyc_taxi LIMIT 1000
```

The code df.select("vendorID", "tripDistance", "fareAmount", "tipAmount").show(5) is used to display the first five rows of a DataFrame called df, and only the columns named: "vendorID", "tripDistance", "fareAmount", "tipAmount". This is a useful function when working with large datasets to quickly inspect the data and ensure that it has been loaded correctly.

`df.select("vendorID", "tripDistance", "fareAmount", "tipAmount").show(5)`

When working with data, one of the initial tasks is to read it into the environment for analysis. Once the data is loaded, basic analysis such as filtering, sorting, and aggregating can be performed. However, as the scale and complexity of the data increase, there is a need for more advanced data engineering scenarios such as data cleansing, transformation, and aggregation. 


# Task 2.3 Import Notebook



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











> [!IMPORTANT]
> Once completed, go to [Exercise 3](./../exercise-3/exercise-3.md) or continue with [Advanced steps below](#advanced-steps).


# Advanced steps

# Medallion architecture
A Medallion architecture is a data design pattern used to organize data in a Lakehouse, with the goal of progressively improving the quality and structure of the data as it flows through each layer of the architecture, starting from the Bronze layer, then to the Silver layer, and finally to the Gold layer.

![image-alt-text](https://techcommunity.microsoft.com/t5/image/serverpage/image-id/243714iAF59794D11862CC4/image-dimensions/521x259?v=v2)

This incremental and progressive improvement enables you to maintain data quality and structure while also improving data processing performance. Medallion architectures are sometimes referred to as "multi-hop" architectures because data flows through multiple layers.

One of the main benefits of a Lakehouse architecture is that it provides a simple data model that is easy to understand and implement. Additionally, it enables incremental ETL (extract, transform, load) operations, which means you can add new data to the Lakehouse in a scalable and manageable way.

Another benefit of a Lakehouse architecture is that it allows you to recreate your tables from raw data at any time. This is possible because Delta Lake provides ACID transactions and time travel capabilities, allowing you to track changes to your data and easily roll back to previous versions if necessary.

Read more [here](https://techcommunity.microsoft.com/t5/analytics-on-azure-blog/simplify-your-lakehouse-architecture-with-azure-databricks-delta/ba-p/2027272).


## Medallion architecture in Fabric Lakehouse

After performing data cleaning and transformation on your Lakehouse data, you can save the resulting data back to another Lakehouse to reflect the "bronze->silver->gold" pattern.

Here's an example code snippet that shows how you can write data to another Lakehouse:


```python
# read data from the bronze Lakehouse
bronze_df = spark.read.table("bronze_lakehouse_name.lakehouse_table")

# perform data cleaning and transformation
# ...

# write the transformed data to the silver Lakehouse
transformed_df.write.format("delta").mode("overwrite").saveAsTable("silver_lakehouse_name.lakehouse_table")
```

In this example, we first read data from the bronze Lakehouse using the spark.read method. We then perform data cleaning and transformation on the bronze_df DataFrame. Finally, we write the transformed data to the silver Lakehouse using the transformed_df.write method, specifying the path to the silver Lakehouse and setting the save mode to "overwrite" to replace any existing data.

> [!IMPORTANT]
> Once completed, go to [Exercise 3](./../exercise-3/exercise-3.md).