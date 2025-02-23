# Homework 3a: Azure Synapse Workspace and Parquet Files Creation

## Objective

In this assignment, we are getting back to our NHTSA data where you will begin working with Azure Synapse Analytics and utilize its SQL Serverless pools powered by a Massively Parallel Processing (MPP) engine. Your task is to prepare your data by converting the NHTSA Complaints File into a `.parquet` format suitable for distributed systems and datasets (sharding). This process simulates the preparation needed to connect to data using Polybase and read directly from the Data Lake. In Homework 7, you will connect to this data as an external table. The main objective of this assignment is to create an Azure Synapse Workspace and partition `.parquet` files by manufacturer name.

## Tasks

### 1. Upgrade Your Storage Account

To link your **Synapse Workspace** to a storage account, it may need to be **upgraded to Azure Data Lake Storage (ADLS) Gen 2** if it wasn't set up during the initial deployment. If your storage account is not already upgraded, follow these steps:

   1. **Navigate to your Storage Account** in the Azure Portal.
   2. In the **left-hand menu**, go to **Settings** > **Data Lake Gen2 upgrade**.
   3. Click **Review and agree to changes** to proceed with the upgrade.
   4. **Validate your account** to check for any features that may not be supported.
      - ⚠ **If you see an error related to `containerDeleteRetentionPolicy`, follow these steps to fix it:**
        - Go to **Data management** > **Data protection** in your storage account.
        - Locate any **Container delete retention policy** setting and **disable all of them**.
        - Save the changes.
        - Return to **Settings** > **Data Lake Gen2 upgrade** and retry the **Start validation** process.
   5. Once validation is complete, **start the upgrade** process.
      - Note: The upgrade may take some time, and your storage account will be temporarily offline.
   6. After the upgrade, confirm that **Hierarchical Namespace** is enabled under **Configuration**.

Once your storage account is upgraded, proceed to the next step of the assignment.

### 2. Convert the NHTSA TXT File to Parquet Format

Use Azure Data Factory (ADF) Data Flows to perform the following steps:

1. **Set Up a Data Flow**:
   - Configure the NHTSA TXT file as the data source.

2. **Configure the Sink**:
   - Set the output format to `.parquet`.

3. **Partition the Parquet Files**:
   - Partition the `.parquet` files by the manufacturer name.
   - **Important**: Some manufacturer names may end with a period (.), which is not allowed in storage account names. Use a filter operator in your data flow to exclude these entries.
   - Refer to the [Complaints Reference File](https://static.nhtsa.gov/odi/ffdd/cmpl/Import_Instructions_Excel_All.pdf) for field details.

### 3. Create Your Synapse Workspace

Set up your Azure Synapse Workspace by following these steps:

1. **Create the Synapse Workspace**:
   - Refer to this [tutorial](https://learn.microsoft.com/en-us/azure/synapse-analytics/get-started-create-workspace) for detailed instructions.
   - **Note**: Do not use the sample data provided in the tutorial.

2. **Link Your Storage Account**:
   - In the Data section of the Synapse Workspace, add your storage account as a linked service if not already connected.
   - Ensure the primary storage account is correctly set up as ADLS Gen 2.

### 4. Utilize the Created Parquet File

Ensure the `.parquet` files created from the NHTSA data are accessible in your Synapse Workspace. This will be essential for the subsequent homework.

## Expectation

> Upon completion, your output should look like the following image.

1. **Synapse Workspace**:
   - <img src="../../images/hw3a/hw6-synapse.png" alt="Screenshot" width="400">

2. **Storage Container**:
   - <img src="../../images/hw3a/hw6-data.png" alt="Screenshot" width="400">


### Additional Resources
- [Tutorial: Write to a Data Lake](https://learn.microsoft.com/en-us/azure/data-factory/tutorial-data-flow-write-to-lake)

Ensure all steps are completed accurately and verify that the `.parquet` files are correctly partitioned and accessible from your Synapse Workspace. Reach out to your LF if you have any questions or need further assistance.

###NSuggested: 
- More information about Polybase a.k.a. Data Virutalization [here:](https://learn.microsoft.com/en-us/sql/relational-databases/polybase/polybase-guide?view=sql-server-ver16)
- More about Parquet: [here:]{https://www.databricks.com/glossary/what-is-parquet}
