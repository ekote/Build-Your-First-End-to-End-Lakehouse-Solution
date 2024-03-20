# Exercise 5 - Latest Fabric Features and Extra Exercises

> [!NOTE]
> Timebox: 40 minutes
> 
> Back to [Agenda](./../README.md#agenda)

# Task 5.1 Stay Updated and Bookmark Essentials
Dive into the latest and greatest from Fabric
* **Monthly Digests**: Don't miss out! Head over to the [Fabric Monthly Updates](https://blog.fabric.microsoft.com/en-us/blog/category/monthly-update) and catch up on the past three months' worth of updates. Discover the latest features and improvements rolled out each week, compiled neatly for your convenience. Bookmark this page to keep your knowledge fresh and up-to-date.
* **Latest Announcements**: Stay in the loop with the most recent news on [Fabric's Blog](https://blog.fabric.microsoft.com/en-US/blog). Here, major updates, like the management of private endpoint capabilities, are discussed in detail. It's a treasure trove of insights and announcements you won't want to miss.
* **Pin the Visualizations**: Show some love for the internal Microsoft team's creative endeavor at [Fabric Notes](https://microsoft.github.io/fabricnotes/). They've brilliantly visualized common concepts in Fabric, earning well-deserved kudos. Pin this website for a blend of inspiration and innovation.
* **Voice Your Ideas**: At Fabric, your voice matters. If there's something you'd like to see improved or introduced, express your ideas on [Fabric Ideas](https://ideas.fabric.microsoft.com/). Tailor your suggestions to specific workloads for clarity. We're all ears and ready to adapt our semester plans to meet your needs. This shift from reactive to proactive engagement empowers you to influence Fabric's future direction. An outstanding instance of this is the introduction of experimental runtimes following your feedback. So, why wait? Share your thoughts and be a part of shaping Fabric's evolution.


## Task 5.1 PIVOT & Experimental Public Preview of Runtime 1.3
* Review The newest runtime version https://learn.microsoft.com/en-us/fabric/data-engineering/runtime-1-3 . The Fabric runtime 1.3 experimental stage gives you early access to new features and Apache Spark APIs. This includes Spark 3.5, which is a Long-Term Support (LTS) version.

This is also a great opportunity for me to share with you that please always use the lastest GA runtime version. Experiment with Preview. But for production local workload use GA version. At the same time, soon we will publish the lifecycle for runtimes. We aim to introduce neuron six months, And also the natural consequence for Spark Is that we'll have to run Deprecation of outdated, unsupported runtimes. Migrate Your production workouts before The depreciation date, Because Once the runtime is depreciated, There is no way to create new pools, And your jobs will be disabled within 90 days after deprecation. 

In this exercise, I want to show you how to refactor a code that we have created previously based on runtime 1.2 (By the way, we didn't have to figure out anything, Because by default, all the workspaces are based on the latest GA version of our runtimes). Runtime 1.2 is based on Spark 3.4. Runtime 1.3 is based on Spark 3.5. 

TODO - table here. 

## 1. Switch to Experimental Public Preview Runtime version 1.3
Use the following instructions to integrate runtime 1.3 into your workspace and use its new features:

Navigate to the Workspace settings tab within your Fabric workspace.
Go to Data Engineering/Science tab and select Spark Settings.
Select the Environment tab.
Under the Runtime Versions dropdown, select 1.3 Experimental (Spark 3.5, Delta 3 OSS) and save your changes. This action sets 1.3 as the default runtime for your workspace.

## 2. Create a new notebook

## 3. Table comparing Spark 3.4 and Spark 3.5

## 4. Run improvements 

## 5. Closing note 

As you can see, Each new Runtime version brings more extensive APIs, More methods, More transformations. Moreover, Once the runtime will hit the stage, Almost Always the newest GA around time version is almost always faster than the previous Generation. Why? Because of improvements that the open source team, but also the internal Microsoft team, synapse and fabric product group, Are working on delivering.


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
Your mission, in that task, involves guiding new team members through the labyrinth of big data processing, particularly in leveraging Apache Spark over Pandas for substantial datasets. This advice is pivotal not only within the Fabric ecosystem but universally in the big data domain.

### Understanding Pandas:
Pandas shines due to its simplicity and intuitive design, making it a favorite among data engineers, scientists, and analysts. However, its primary limitation lies in its inability to natively harness parallel architectures and computations. Pandas operates within the confines of single-node, in-memory computations, restricting its scalability and efficiency in processing vast datasets typical in big data scenarios.

### Transition to Spark and its core concepts:
Apache Spark transcends these limitations by adopting a distributed computing approach. Key distinctions include:
- **Spark DataFrames**: These are distributed across clusters, enabling parallel data processing far beyond the capacities of a single machine.
- **Lazy Evaluation**: Spark employs lazy evaluation for DataFrames, constructing a Directed Acyclic Graph (DAG) of transformations that are optimized and executed only when an action is required, enhancing overall execution efficiency.
- **Advanced Optimizations**: Features like Adaptive Query Execution (AQE) and Dynamic Partition Pruning (DPP) automatically optimize query plans and data partitioning, respectively, something far beyond the reach of Pandas.

### General rule of thumb:
- Utilize Pandas for datasets that comfortably fit into the memory of a single machine and when the data processing doesn't demand extensive parallelization.
- Opt for Spark when dealing with massive datasets that exceed single machine capacity, or when tasks benefit significantly from parallelization, despite any existing familiarity with Pandas due to Spark's scalability and optimization features.

### Bridging the gap with Koalas:
Introduced in Spark 3.2, Koalas marries the simplicity of the Pandas API with Spark’s distributed computing prowess. By importing `pandas` API through PySpark:

```python
from pyspark import pandas as pd
```

This integration enables data practitioners to apply familiar Pandas-like operations while leveraging Spark's distributed architecture, achieving the best of both worlds.

### Practical application in Fabric:
In Fabric, data loading practices vary between Pandas and Spark. Below is an example demonstrating how to load a CSV file into both frameworks. This comparison not only highlights syntax differences but also emphasizes when to employ each framework based on dataset size and computational needs.

By the end of this task, you should be able to discern the appropriate circumstances for utilizing Pandas versus Spark, ensuring optimal data processing strategies in your big data endeavors.


Proceed to your next challenge, which will delve deeper into Pandas, enriching your data manipulation skills in big data contexts.


## Task 5.6 Data Wrangler is my friend
Immerse yourself in the world of efficient data analysis with Fabric's Data Wrangler. This task is designed to help you leverage Data Wrangler's capabilities to explore and transform Pandas DataFrames effectively. Data Wrangler blends a user-friendly grid-like interface with dynamic data analysis tools, making exploratory data analysis both intuitive and robust.

Dive deep into the functionalities of Data Wrangler within Fabric, focusing specifically on Pandas DataFrames. Your task will be segmented into actionable steps, guiding you through the process of data exploration, visualization, and transformation within this powerful tool.

Step-by-Step Instructions:

### Initial Setup
Open your Fabric environment and navigate to the Data Wrangler tool within your notebook.
Load a Pandas DataFrame that you wish to analyze. If you don't have a specific dataset in mind, utilize a sample dataset provided within the platform.

#### Exploratory Data Analysis

Utilize the grid-like data display to review your dataset. Pay attention to the distribution of data, missing values, and data types.
Generate dynamic summary statistics to gain quick insights into the mean, median, mode, min, and max of your data columns.
Leverage built-in visualizations to understand data distributions, correlations, and outliers. Experiment with different chart types to best represent your data.
#### Data Cleaning Operations

Identify any inconsistencies, missing values, or outliers within your dataset.
Apply common data-cleaning operations available in Data Wrangler, such as filling missing values, filtering rows, or correcting data types. Observe how each operation updates the data display in real time.
Evaluate the impact of your data transformations on the summary statistics and visualizations to ensure they align with your analysis goals.

#### Code Generation and Reusability

As you apply transformations within Data Wrangler, observe the automatic generation of corresponding code in either Pandas or PySpark.
Save the generated code back to your notebook as a reusable function. This practice not only enhances your understanding of data transformations but also builds a library of custom functions for future analysis.


#### Documentation and Reflection

Document each step of your exploratory data analysis and data cleaning process within the notebook. Include insights gained, reasons behind specific transformations, and how the changes impact the overall data analysis.
Reflect on the ease of use, functionalities, and any limitations you encountered while using Data Wrangler. Consider how these aspects can influence your data analysis workflows in future projects.


TODO VIDEO

TODO SCREENSHOTS 


## Task 5.7 Single Node Cluster
* [ ] Review https://learn.microsoft.com/en-us/fabric/data-engineering/spark-compute#spark-pools




## Task 5.8 Managed Private Endpoints
* [ ] Review https://learn.microsoft.com/en-us/fabric/security/security-managed-private-endpoints-overview 


## Task 5.9 VSCode (APP and WEB)







> [!IMPORTANT]
> Once completed, go to [Agenda](./../README.md#agenda). If time permits before the next exercise begins, consider continuing with [Advanced steps](./../extra/extra.md).