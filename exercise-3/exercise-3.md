# Exercise 3 - Organize, secure, and prepare data using schemas, permissions, and projects

> [!NOTE]
> Timebox: 30 minutes
> 
> Back to [Agenda](./../README.md#agenda)
> 
> Back to [Exercise 2](./../exercise-2/exercise-2.md)

```
?? TODO
1.	(DEMO) Azure Data Studio / SSMS
1.1.	Use T-SQL (SQL Endpoint) to play with some data from OneLake (Lakehouse)
2.	Workspace access management
3.	Sharing
3.1.	Share lakehouse
3.2.	share notebook
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
### Sharing a Lakehouse

To share a Lakehouse, click the <b>Share</b> button next to the lakehouse name in the <b>Workspace</b>. 

![LakehouseShare](https://github.com/ekote/Build-Your-First-End-to-End-Lakehouse-Solution/assets/63069887/f33d4f80-d24e-4804-b81f-ea4fd2f3188d)

This will open the <b>Sharing dialog</b>
1. Enter name or email address of users who you want to share the Lakehouse with.
2. Check the boxes to grant appropriate permissions. Lakehouse sharing by default grants lakehouse, associated SQL endpoint, and default semantic model.
3. To send a mail check the box <b>"Notify recipients by mail"</b>. Include an optional message.
4. Click <b>Grant</b>.

![LakehouseSharingDialog](https://github.com/ekote/Build-Your-First-End-to-End-Lakehouse-Solution/assets/63069887/b7d04784-d5c6-44d9-accb-4e7119d6fea8)



### Task 5
### Sharing a Notebook

Sharing a notebook is a convenient way for you to collaborate with team members. You can share a notebook with specified permissions granted.
1. Open the notebook to be shared. Select <b>Share</b> on the notebook toolbar.

![image](https://github.com/ekote/Build-Your-First-End-to-End-Lakehouse-Solution/assets/63069887/496e0f19-3d63-4e6f-9698-1adcbdf2f052)

2. Select the corresponding category of <b>people who can view this notebook</b>. You can choose <b>Share, Edit, or Run</b> permissions for the recipients.

![image](https://github.com/ekote/Build-Your-First-End-to-End-Lakehouse-Solution/assets/63069887/f6674e9e-791e-4f7b-84b6-43b2140e0e6d)

3. After you select <b>Apply</b>, you can either send the notebook directly or copy the link to others. Recipients can then open the notebook with the corresponding view granted by their permission level.

![image](https://github.com/ekote/Build-Your-First-End-to-End-Lakehouse-Solution/assets/63069887/0a097d72-0a5e-4617-8920-6fd0439d8cad)

5. To further manage your notebook permissions, select Workspace item list > More options, and then select Manage permissions. From that screen, you can update the existing notebook access and permissions.

![image](https://github.com/ekote/Build-Your-First-End-to-End-Lakehouse-Solution/assets/63069887/b37e8de8-36d8-4a4b-accb-4b67c901f26a)






<!-- ### Task 4
### Objective: Create a workspace managed identity

Creating a workspace identity in Microsoft Fabric involves 3 steps:
1.  **Navigate** to the workspace and open the workspace settings.
2.  Select the **Workspace identity** tab.
3.  Click on the **+ Workspace identity** button to create a new identity.

Once created, the workspace identity details and a list of authorized users will be displayed. The workspace identity is automatically assigned the workspace contributor role and has access to workspace items.
-->

> [!IMPORTANT]
> Once completed, go to [Exercise 4](./../exercise-4/exercise-4.md). If time permits before the next exercise begins, consider continuing with [Advanced steps](./../extra/extra.md).
