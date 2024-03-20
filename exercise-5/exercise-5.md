# Exercise 5 - Latest Fabric Features and Extra Exercises

> [!NOTE]
> Timebox: 40 minutes
> 
> Back to [Agenda](./../README.md#agenda)

# Task 5.1 Know the Updates and Save the links
* Review monthly updates https://blog.fabric.microsoft.com/en-us/blog/category/monthly-update for the recent three months. Every week there is it a rollout of the new improvements, New features. And the team is gathering all the changes as part of the monthly updates. Tap to your bookmark subject will be always updated. 
* Review recent updates for https://blog.fabric.microsoft.com/en-US/blog - Sometimes there are updates like for example, manage private endpoint capability. Such a big announcement are included into updates blog post.
* Pin The website https://microsoft.github.io/fabricnotes/ Created by the Microsoft internal team, who is proud to build a visualization of the common concept with a fabric. Kudos to them.
* In fabric, we listen to customers needs that's why everyone, including you can suggest the idea that improvement that you want to see in fabric. Please write it here https://ideas.fabric.microsoft.com/ And talk properly according to the workload. We prioritize our features and build a semester plan to answer your needs. I bring it, encourage you to share your idea to switch from reactive to proactive mode when you can impact an influence the product direction. One of the greatest example is the feedback about a new runtimes. That's why during the FabCon We announced a new stage of runtime named experimental. The first task below is exactly about it. 


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
Imagine your new team members wrote a lot of Pandas code and run it on big cluster Based on Apache Spark. Your task is to explain the best practices to Your colleague About processing big data Fabric and in general, As those rules applied everywhere.

Pandas is simple. Data engineers, data, scientists data, analysts everyone loves pandas. The biggest limitation for pandas Is that it Doesn't understand Paraller architecuter and computations. Meaning that advance on a single machine, I'm a single node.

Now a note about Spark and the core concept under spark - Data frames
Spark Dataframes work in distributed manned compared to Pandas Dataframes.  Spark Dataframes are lazily evaluated which basically means that it doesn't execute until and unless an action is called and all the transformations that you have provided are created into a DAG. When you use Spark Dataframes, all the steps that you have mentioned before executions are converted into an optimized plan by Spark itself and you get many other capabilities like AQE(Adaptive Query Execution),DPP (Dynamic Partition Pruning) and much more than a Pandas dataframe can provide.

So the general rule is:
> If the data is small enough that you can use pandas to process it, then you likely don't need pyspark. Spark is useful when you have such large data sizes that it doesn't fit into memory in one machine since it can perform distributed computation. That being said, if the computation is complex enough that it could benefit from a lot of parallelization, then you could see an efficiency boost using pyspark. I'm more comfortable with pyspark's APIs than pandas, so I might end up using pyspark anyways, but whether you'll see an efficiency boost depends a lot on the problem.

There is one innovation, That there is no week without a question about it.

Starting from Spark 3.2, Koalas has become a part of Spark. In PySpark, you can utilize the pandas API, by using:

from pyspark import pandas as pd

So now we can use pandas API in spark. We can leverage parallel, computations use of the beautiful and simple syntax. 

In fabric a couple of ways how you can Get the code for pandas. One of them is by loading for example CSV file. Please take a look at the example of the screen how we can load to the CSV either to pandas or spark. After this task, I am certain that you know which tool you should use. 

Let's go to the next Task which is very about pandas.

## Task 5.6 Data Wrangler is my friend
TODO VIDEO

SLIDES HOW TO

Let's continue discussion about pandas because as mentioned, The original pandas just need one node. Now let's jump to the hardware configuration to optimize for panda computation, At the same time, not over invest. 

## Task 5.7 Single Node Cluster
* [ ] Review https://learn.microsoft.com/en-us/fabric/data-engineering/spark-compute#spark-pools




## Task 5.8 Managed Private Endpoints
* [ ] Review https://learn.microsoft.com/en-us/fabric/security/security-managed-private-endpoints-overview 


## Task 5.9 VSCode (APP and WEB)







> [!IMPORTANT]
> Once completed, go to [Agenda](./../README.md#agenda). If time permits before the next exercise begins, consider continuing with [Advanced steps](./../extra/extra.md).