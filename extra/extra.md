> [!NOTE]
> 
> Back to [Agenda](./../README.md#agenda) | [Start Steps](./../start/start.md) | [Exercise 1](./../exercise-1/exercise-1.md) | [Exercise 2](./../exercise-2/exercise-2.md) | [Exercise 3](./../exercise-3/exercise-3.md) | [Exercise 4](./../exercise-4/exercise-4.md) | [Exercise 5](./../exercise-5/exercise-5.md)

# List of extra exercises
## Specify the file format and compression type for the sink datasets in Data Factory
## Monitor the pipeline run and verify the output
## Create a dataflow that reads data from a CSV file
## Medallion architecture
## Schedule your notebook
## Create a new Spark Pool on the Workspace-level settings
## Use Environment to tailor your runtime
## Saved with V-Order?

---

# Specify the file format and compression type for the sink datasets in Data Factory
![Compression](./../media/extra/1.jpg)
![Compression](./../media/extra/2.jpg)

---

# Monitor the pipeline run and verify the output
![Monitoring](./../media/extra/3.jpg)
![Monitoring](./../media/extra/4.jpg)
![Monitoring](./../media/extra/5.jpg)
![Monitoring](./../media/extra/6.jpg)
![Monitoring](./../media/extra/7.jpg)
![Monitoring](./../media/extra/8.jpg)
![Monitoring](./../media/extra/9.jpg)

# Create a dataflow that reads data from a CSV file


---

# Medallion architecture
A Medallion architecture is a data design pattern used to organize data in a Lakehouse, with the goal of progressively improving the quality and structure of the data as it flows through each layer of the architecture, starting from the Bronze layer, then to the Silver layer, and finally to the Gold layer.

![image-alt-text](https://techcommunity.microsoft.com/t5/image/serverpage/image-id/243714iAF59794D11862CC4/image-dimensions/521x259?v=v2)

This incremental and progressive improvement enables you to maintain data quality and structure while also improving data processing performance. Medallion architectures are sometimes referred to as "multi-hop" architectures because data flows through multiple layers.

One of the main benefits of a Lakehouse architecture is that it provides a simple data model that is easy to understand and implement. Additionally, it enables incremental ETL (extract, transform, load) operations, which means you can add new data to the Lakehouse in a scalable and manageable way.

Another benefit of a Lakehouse architecture is that it allows you to recreate your tables from raw data at any time. This is possible because Delta Lake provides ACID transactions and time travel capabilities, allowing you to track changes to your data and easily roll back to previous versions if necessary.

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

Our real case, one more time:

```python
table_name  = "green201501"

data_collection = table_name[:-6]  # Extracts all characters except the last six (assumes these are non-digits)
extracted_year = table_name[-6:-2]  # Extracts the four digits representing the year
extracted_month = table_name[-2:]  # Extracts the last two digits representing the month

from pyspark.sql.functions import col, year, month, dayofmonth, avg

# !!!!
# READING RAW DATA FROM DEFAULT (RAW) LAKEHOUSE
df = spark.read.table(table_name)

# Calculate average fare amount per month
average_fare_per_month = (
    df
    .groupBy(year("lpep_pickup_datetime").alias("year"), month("lpep_pickup_datetime").alias("month"))
    .agg(avg("fare_amount").alias("average_fare"))
    .orderBy("year", "month")
)
display(average_fare_per_month)

result_table_name = f"{table_name}_avg_fare_per_month"

# Save the results to a new delta table - SILVERCLEANSED LAKEHOUSE - SILVER LAYER
average_fare_per_month.write.format("delta").mode("overwrite").saveAsTable(f"silvercleansed.{result_table_name}")
```

![Medallion Architecture](./../media/1/medarch.jpg)

## Medallion Architecture Data Design and Lakehouse Patterns | Microsoft Fabric Data Factory

Watch Fabric Espresso episode as Abhishek discuss and demo the Medallion Architecture Data Design and Lakehouse Patterns in Microsoft Fabric Data Factory.  
[![FabricEspresso](https://img.youtube.com/vi/706MVIBivOU/0.jpg)](https://www.youtube.com/watch?v=706MVIBivOU)

Task: 

---

# Schedule your notebook
Your task is to schedule notebook to run every hour.
Save, schedule and run the notebook as a job 

![Monitoring](./../media/extra/10.jpg)
![Monitoring](./../media/extra/11.jpg)


## Create a new Spark Pool on the Workspace-level settings
![Monitoring](./../media/extra/12.jpg)
![Monitoring](./../media/extra/13.jpg)
![Monitoring](./../media/extra/14.jpg)
![Monitoring](./../media/extra/15.jpg)
![Monitoring](./../media/extra/16.jpg)
![Monitoring](./../media/extra/17.jpg)


## Use Environment to tailor your runtime
![Monitoring](./../media/extra/18.jpg)
![Monitoring](./../media/extra/19.jpg)
![Monitoring](./../media/extra/20.jpg)
![Monitoring](./../media/extra/21.jpg)
![Monitoring](./../media/extra/22.jpg)
![Monitoring](./../media/extra/23.jpg)
![Monitoring](./../media/extra/24.jpg)

## Saved with V-Order?
![Monitoring](./../media/extra/25.jpg)
![Monitoring](./../media/extra/26.jpg)
![Monitoring](./../media/extra/27.jpg)


## DW vs Lakehouse?
![DW or Lakehouse](https://microsoft.github.io/fabricnotes/images/notes/04-lakehouse-vs-warehouse.png)

![Two endpoints](https://microsoft.github.io/fabricnotes/images/notes/12-sql-endpoints.png)

## SaaS vs PaaS
* ![Fabric Basic](https://microsoft.github.io/fabricnotes/images/notes/03-fabric-saas-product.png)

## Fabric Licensing
* ![Fabric Licensing](https://microsoft.github.io/fabricnotes/images/notes/13-fabric-licensing.png)

## Fabric UI
* ![Fabric Basic](https://microsoft.github.io/fabricnotes/images/notes/02-understand-fabric-ui.png)

## Fabric Capacities
* ![Fabric Basic](https://microsoft.github.io/fabricnotes/images/notes/08-fabric-lingo-part-1.png)
