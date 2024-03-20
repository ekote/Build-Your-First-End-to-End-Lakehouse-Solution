# Advanced Tasks for Exercise 1

##  Task 1.2 Use a Copy Data activity to configure the source and sink datasets, and specify the file format and compression type.

## Task 1.3 Monitor the pipeline run and verify the output files in the data lake.

## Task 1.4 Create a dataflow that reads data from a CSV file in the data lake and performs some transformations, such as filtering, joining, aggregating, and mapping.

## Task 1.5 Use the data preview and debug features to inspect the data at each step of the transformation.
Write the transformed data to a Delta table in the Lakehouse.

## Task 1.6 Run the dataflow and monitor the Spark job execution details. 

> [!IMPORTANT]
> Once completed, go to [Exercise 2](./../exercise-2/exercise-2.md).

# Advanced Tasks for Exercise 2








# Task 2.6 Transform the data using Spark SQL and PySpark APIs
Your task is to factory the code produced by your colleague. 


# Task 2.7 Schedule notebook
Your task is to schedule notebook to run every hour.

Save, schedule and run the notebook as a job 

# Task 2.8 Workspace-level settings

# Task 2.9 Compute Settings


# Task 2.10 Environment


# Task 2.11 GIT


# Task 2.12 Saved with V-Order?


# Task 2.13 DW vs Lakehouse?
![DW or Lakehouse](https://microsoft.github.io/fabricnotes/images/notes/04-lakehouse-vs-warehouse.png)



![Two endpoints](https://microsoft.github.io/fabricnotes/images/notes/12-sql-endpoints.png)


# Task 2.15 Run OPTIMIZE cmd

# Task 2.16 CODE REVIEW in shared notebook


##  Medallion architecture
A Medallion architecture is a data design pattern used to organize data in a Lakehouse, with the goal of progressively improving the quality and structure of the data as it flows through each layer of the architecture, starting from the Bronze layer, then to the Silver layer, and finally to the Gold layer.

![image-alt-text](https://techcommunity.microsoft.com/t5/image/serverpage/image-id/243714iAF59794D11862CC4/image-dimensions/521x259?v=v2)

This incremental and progressive improvement enables you to maintain data quality and structure while also improving data processing performance. Medallion architectures are sometimes referred to as "multi-hop" architectures because data flows through multiple layers.

One of the main benefits of a Lakehouse architecture is that it provides a simple data model that is easy to understand and implement. Additionally, it enables incremental ETL (extract, transform, load) operations, which means you can add new data to the Lakehouse in a scalable and manageable way.

Another benefit of a Lakehouse architecture is that it allows you to recreate your tables from raw data at any time. This is possible because Delta Lake provides ACID transactions and time travel capabilities, allowing you to track changes to your data and easily roll back to previous versions if necessary.

Read more [here](https://techcommunity.microsoft.com/t5/analytics-on-azure-blog/simplify-your-lakehouse-architecture-with-azure-databricks-delta/ba-p/2027272).


### Medallion architecture in Fabric Lakehouse

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

## Medallion Architecture Data Design and Lakehouse Patterns | Microsoft Fabric Data Factory

Watch Fabric Espresso episode as Abhishek and Estera discuss the Medallion Architecture Data Design and Lakehouse Patterns in Microsoft Fabric Data Factory.  

[![FabricEspresso](https://img.youtube.com/vi/706MVIBivOU/0.jpg)](https://www.youtube.com/watch?v=706MVIBivOU)



## Deployments Pipelines


## Rest API




## MS SPARK UTILITIES - run another notebook reference run

TODO VIDEO

## Run multiple

> [!IMPORTANT]
> Once completed, go to [Exercise 3](./../exercise-3/exercise-3.md).



# Advanced Tasks for Exercise 3


> [!IMPORTANT]
> Once completed, go to [Exercise 4](./../exercise-4/exercise-4.md).

# Advanced Tasks for Exercise 4

> [!IMPORTANT]
> Once completed, go to [Exercise 5](./../exercise-5/exercise-5.md).


# Advanced Tasks for Exercise 5


# Task 5.5 managed private endpoints for Fabric


# Task 5.7 VSCODE
TODO VIDEO
