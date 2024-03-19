# Exercise 3 - Organize, secure, and prepare data using schemas, permissions, and projects

> [!NOTE]
> Timebox: 30 minutes
> 
> Back to [Agenda](./../README.md#agenda)


```
?? TODO
1.	(DEMO) Azure Data Studio / SSMS
1.1.	Use T-SQL (SQL Endpoint) to play with some data from OneLake (Lakehouse)
2.	Workspace access management
3.	Sharing
3.1.	Share lakehouse
3.2.	share notebook
4.	VSCode
5.	[*] Enforce RLS thru the SQL endpoint
6.	Create a workspace-managed identity
7.	Create a project and link it to a DevOps repository
```

The **SQL Analytics Endpoint** of a Fabric Lakehouse Offers a SQL-based experience for analyzing data in lakehouse delta tables using T-SQL language, with features like saving functions, generating views, and applying SQL security.

When a lakehouse is shared, users are automatically granted Read permission, which applies to the lakehouse itself, the linked SQL endpoint, and the default semantic model. Beyond this standard access, users may also be granted:

-   **ReadData** permission for the SQL endpoint, enabling data access without the enforcement of SQL policies.
-   **ReadAll** permission for the lakehouse, allowing comprehensive data access via Apache Spark.
-   **Build** permission for the default semantic model, permitting the creation of Power BI reports utilizing this model
  

### Task 1
### Objective: Get the Lakehouse SQL Analytics Endpoint Connection String 

To retrieve the SQL connection string for a Lakehouse SQL analytics endpoint you can follow these steps:

1. Navigate to your workspace, select the Lakehouse SQL analytics endpoint item, and select More options.
2. Select Copy SQL connection string to copy the connection string to your clipboard.
3. Once you have the connection string, you can use it to connect to your SQL analytics endpoint or Warehouse using tools like SQL Server Management Studio or Azure Data Studio.

### Task 2
### Objective: Connect to a Fabric SQL Endpoint using SQL Server Management Studio (SSMS)

To connect to a Fabric SQL Endpoint using SQL Server Management Studio (SSMS), you can follow these steps:

1. Open SSMS and the Connect to Server window should appear. If it’s already open, go to Object Explorer > Connect > Database Engine.
2. In the Server name box, paste the SQL connection string you copied earlier.
3. Click Connect and select Microsoft Entra multifactor authentication (MFA).
4. Enter your workshop user email or your enterprise email id.
5. Once connected, Object Explorer will display the connected lakehouses from your workspace, along with its tables and views, ready for querying.

### Task 3
### Objective: Execute TSQL Queries on Lakehouse Delta Tables

##### 1. Get the count of rows in NYC Taxi table
```
SELECT COUNT(*)
FROM [FabricCClkh001].[dbo].[nyctaxi_green]
```
##### 2. Get Average Fare and Tip Amount
```
SELECT ROUND(AVG([fareAmount]),2) AS [Average Fare], 
ROUND(AVG([tipAmount]),2) AS [Average Tip] 
FROM [FabricCClkh001].[dbo].[nyctaxi_green]
```

##### 3. Get Average Fares and Total Fares by Passenger Count
```
SELECT DISTINCT [passengerCount], 
ROUND(SUM ([fareAmount]),0) as TotalFares,
ROUND (AVG ([fareAmount]),0) as AvgFares
FROM [FabricCClkh001].[dbo].[nyctaxi_green]
GROUP BY [passengerCount]
ORDER BY  AvgFares DESC
```
##### 4. Get Compare Tipped vs Not Tipped trip numbers
```
SELECT tipped, COUNT(*) AS tip_freq FROM (
  SELECT CASE WHEN (tipAmount > 0) THEN 1 ELSE 0 END AS tipped, tipAmount
  FROM [FabricCClkh001].[dbo].[nyctaxi_green]
  WHERE [lpepPickupDatetime] BETWEEN '20130101' AND '20131231') tc
GROUP BY tipped
```

### Task 4
### Objective: Create a workspace managed identity

Creating a workspace identity in Microsoft Fabric involves 3 steps:
1.  **Navigate** to the workspace and open the workspace settings.
2.  Select the **Workspace identity** tab.
3.  Click on the **+ Workspace identity** button to create a new identity.

Once created, the workspace identity details and a list of authorized users will be displayed. The workspace identity is automatically assigned the workspace contributor role and has access to workspace items.


> [!IMPORTANT]
> Once completed, go to [Exercise 4](./../exercise-4/exercise-4.md) or continue with [Advanced steps below](#advanced-steps).


# Advanced steps





> [!IMPORTANT]
> Once completed, go to [Exercise 4](./../exercise-4/exercise-4.md).