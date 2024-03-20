> [!NOTE]
> 
> Back to [Agenda](./../README.md#agenda)

# Exercise 1 - Extra Tasks

# Task 5.3 Browse Azure resources with Get Data
Source: https://blog.fabric.microsoft.com/en-us/blog/browse-azure-resources-with-get-data?ft=All

With the new ‘browse Azure’ functionality in Get Data, you can easily browse all your Azure resources and automatically connect to them, without going through manually setting up a connection, saving you a lot of time.

Using the regular path in Get Data to create a new connection, you always need to fill in your endpoint, URL or server and database name when connecting to Azure resources like Azure Blob, Azure Data Lake gen2 and Synapse. This is a bit of a tedious process and does not allow for easy data discovery.

Supported data sources:
* Azure Blob
* Azure Data Lake gen 2
* Synapse

When cover you to try Functionality on your own. Why? Because it is The best way to access the data of our synapse from the factory. In this task, you do not need to do anything. I'd rather acknowledge that newest functionality. The question I would like to leave you with is:
* For those who has the synapse workload - How we can plan, And execute efficient migration to fabric? You may ask me why do I need it? That's why I included the video with Guy, Product manager accountable for hardware, spark compute, And he's explaining that we just movement to fabric, Your workload will run faster. Why? Because synapse is mostly based on The hardware SKU Which is older comparing to fabric skU. And with the new SKU There are improvements for CPR and memory management. This elements have the biggest impact to run your spark computation Faster. 

##  Task 1.2 Use a Copy Data activity to configure the source and sink datasets, and specify the file format and compression type.

## Task 1.3 Monitor the pipeline run and verify the output files in the data lake.

## Task 1.4 Create a dataflow that reads data from a CSV file in the data lake and performs some transformations, such as filtering, joining, aggregating, and mapping.

## Task 1.5 Use the data preview and debug features to inspect the data at each step of the transformation.
Write the transformed data to a Delta table in the Lakehouse.

## Task 1.6 Run the dataflow and monitor the Spark job execution details. 

> [!IMPORTANT]
> Once completed, go to [Exercise 2](./../exercise-2/exercise-2.md).




# Exercise 2 - Extra Tasks

## Task 2.6 Transform the data using Spark SQL and PySpark APIs
Your task is to factory the code produced by your colleague. 


## Task 2.7 Schedule notebook
Your task is to schedule notebook to run every hour.

Save, schedule and run the notebook as a job 

## Task 2.8 Workspace-level settings

## Task 2.9 Compute Settings


## Task 2.10 Environment


## Task 2.11 GIT


## Task 2.12 Saved with V-Order?


## Task 2.13 DW vs Lakehouse?
![DW or Lakehouse](https://microsoft.github.io/fabricnotes/images/notes/04-lakehouse-vs-warehouse.png)



![Two endpoints](https://microsoft.github.io/fabricnotes/images/notes/12-sql-endpoints.png)


## Task 2.15 Run OPTIMIZE cmd

## Task 2.16 CODE REVIEW in shared notebook


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



# Exercise 3 - Extra Tasks

> [!IMPORTANT]
> Once completed, go to [Exercise 4](./../exercise-4/exercise-4.md).


# Exercise 4 - Extra Tasks
> [!IMPORTANT]
> Once completed, go to [Exercise 5](./../exercise-5/exercise-5.md).


# Exercise 5 - Extra Tasks

## Task 5.5 managed private endpoints for Fabric


## Task 5.7 VSCODE
TODO VIDEO


# Core

## SaaS vs PaaS
* ![Fabric Basic](https://microsoft.github.io/fabricnotes/images/notes/03-fabric-saas-product.png)


## Fabric Licensing
* ![Fabric Licensing](https://microsoft.github.io/fabricnotes/images/notes/13-fabric-licensing.png)

## Fabric UI
* ![Fabric Basic](https://microsoft.github.io/fabricnotes/images/notes/02-understand-fabric-ui.png)

## Fabric Capacities
* ![Fabric Basic](https://microsoft.github.io/fabricnotes/images/notes/08-fabric-lingo-part-1.png)

## What is Apache Spark
