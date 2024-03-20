# Exercise 5 - Latest Fabric Features and Extra Exercises

> [!NOTE]
> Timebox: 40 minutes
> 
> Back to [Agenda](./../README.md#agenda)

# Task 5.1 Know the Updates and Save the links
* Review monthly updates https://blog.fabric.microsoft.com/en-us/blog/category/monthly-update for the recent three months
* Review recent updates for https://blog.fabric.microsoft.com/en-US/blog 
* Pin https://microsoft.github.io/fabricnotes/
* Pin https://ideas.fabric.microsoft.com/
* ![Fabric Licensing](https://microsoft.github.io/fabricnotes/images/notes/13-fabric-licensing.png)
* ![Fabric Basic](https://microsoft.github.io/fabricnotes/images/notes/03-fabric-saas-product.png)
* ![Fabric Basic](https://microsoft.github.io/fabricnotes/images/notes/02-understand-fabric-ui.png)
* ![Fabric Basic](https://microsoft.github.io/fabricnotes/images/notes/08-fabric-lingo-part-1.png)


## Task 5.1 PIVOT & Experimental Public Preview of Runtime 1.3
* [ ] Review https://learn.microsoft.com/en-us/fabric/data-engineering/runtime-1-3

Always use the lastest GA runtime version. Experiment with Preview. Migrate before it will be too late.


# Task 5.3 Browse Azure resources with Get Data
* [ ] Review https://blog.fabric.microsoft.com/en-us/blog/browse-azure-resources-with-get-data?ft=All


# Task 5.4 Autotune Query Tuning
* [ ] Review https://learn.microsoft.com/en-us/fabric/data-engineering/autotune?tabs=sparksql

> [!TIP]
> Autotune query tuning examines individual queries and builds a distinct ML model for each query. It specifically targets:
> - Repetitive queries
> - Long-running queries (those with more than 15 seconds of execution)
> - Spark SQL queries (excluding those written in the RDD API, which are very rare)
>
> This feature is compatible with notebooks, Spark Job Definitions, and pipelines.


## Task 5.5 Spark vs Pandas
Your new team members wrote a lot of Pandas code and run it on big cluster. Your task is to explain the best practices to process big data.


## Task 5.6 Data Wrangler is my friend
TODO VIDEO

## Task 5.7 Single Node Cluster
* [ ] Review https://learn.microsoft.com/en-us/fabric/data-engineering/spark-compute#spark-pools


## Task 5.8 Managed Private Endpoints
* [ ] Review https://learn.microsoft.com/en-us/fabric/security/security-managed-private-endpoints-overview 


## Task 5.9 VSCode

> [!IMPORTANT]
> Once completed, go to [Agenda](./../README.md#agenda). If time permits before the next exercise begins, consider continuing with [Advanced steps](./../extra/extra.md).