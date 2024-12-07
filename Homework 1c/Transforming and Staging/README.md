# Homework 1c - Transforming and Staging

**Class,**

> **NOTE** - Homework 1c builds on your activities in Homework 1b (Extract and Load). You will be using the same `resource group` and `data-factory` from the previous assignment. If you could not complete Homework 1b due to difficulties, please reach out to LF Office Hours for assistance before starting this assignment.

In Homework 1b, you extracted and loaded a data file into your storage account. For Homework 1c, you will extend that work by transforming and moving data from a `.txt` file into a SQL Server database table. Refer to the appendix of this [reference document](https://static.nhtsa.gov/odi/ffdd/cmpl/Import_Instructions_Excel_All.pdf) for details on datatypes and fields.

## Assignment Overview
Using your existing Data Factory, you will:

1. **Transform**: Convert the `DateA` column datatype from text to date.
2. **Stage**: Load the transformed data into a database table named `<initials>Complaints` within a SQL Server database.

## Steps to Complete Homework 1c

### Step 1: Set Up Your SQL Server and Database
Once again, you should use the `bash fromTemplate.sh` script for creating your SQL Server, using the following command to deploy resources:

```azurecli-interactive
az deployment group create --resource-group <resource-group-name> --template-file <path-to-template.json> --parameters @<path-to-parameters.json>
```

### Step 2: Create Your Database Table
Use the `Complaints Reference File` to set up your table attributes with the correct data types. It is recommended to use `NVARCHAR` for text columns to handle Unicode characters. The reference file specifies the lengths of each of the attributes (colunmns) when defining your database table.

### Step 3: Load Data with Azure Data Factory
1. Use Azure Data Factory to create a pipeline that includes:
   - **Transformation**: Convert the `DateA` column from text to a date (not datetime) format.
   - **Loading**: Insert the data into the `<initials>Complaints` table.

### Step 4: Query and Export Results
After loading the data, run the following query in your SQL Server, making sure to replace the table name with the name you created for your table in your database:

```sql
SELECT *
FROM <cbsComplaints>
WHERE DATEA = CONVERT(Date, GETDATE() - 1)
```

**Note**: The "GETDATE() - 1" is a SQL command specifying Today's date -1 day, aka yesterday. However, if your latest file download is prior to today, or happens to fall on a weekend, you will have to change the "-1" to the most recent day where records exist in the source dataset. (-2, -5, -7, etc for the number of days back)

Output the results to a file and save it as a PDF for submission.

## Reference Documents and Tools
- [Getting Started with Azure Data Factory](https://learn.microsoft.com/en-us/azure/data-factory/quickstart-create-data-factory)
- [Creating a Storage Account](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-create?tabs=azure-portal)
- [Creating a Database in Azure SQL Server Using Your Existing SQL Server](https://learn.microsoft.com/en-us/azure/azure-sql/database/single-database-create-quickstart?view=azuresql&tabs=azure-portal)
- [Creating a Table in an Azure SQL Database](https://www.edureka.co/community/62364/how-to-create-table-in-azure-sql-database)
- [Complaints Data File](https://static.nhtsa.gov/odi/ffdd/cmpl/FLAT_CMPL.zip)
- [Complaints Reference File](https://static.nhtsa.gov/odi/ffdd/cmpl/Import_Instructions_Excel_All.pdf)
- [Copy Tool](https://docs.microsoft.com/en-us/azure/data-factory/copy-activity-overview)
- [Data Flow](https://docs.microsoft.com/en-us/azure/data-factory/concepts-data-flow-overview)

---

## Verification and Submission

Upon completion, submit the following as proof of your work:

1. **Screenshot of Query Execution in Azure SQL Database** 
   - <img src="../../images/hw3/hw3-screenshot.png" alt="Screenshot" width="400">

2. **PDF of SQL Query Output** Typically you can expect approximately a couple hundred records added per day, so if you are getting more, check your query, else, if you have zero, you may need to go back further with your GETDATE command.

Save the screenshots as `.png` or `.jpg` files and upload them through the course submission portal for Homework 1.

---

## Points to Consider 🤔
- How do you use the `Complaints Reference File` to create a table in Azure SQL Database?
- How do you use the `Copy Tool` to load data from Azure Storage to Azure SQL Database?
- How do you handle rows with missing values?
- What happens if the data in the txt file does not adhere to the datatype you've set for your SQL database table?
- What if the header column names differ from table column names?
- What is the current format of the file, the delimiter, and the number of columns?
- How do you map columns and change their data types?

---

Ensure you understand each step and reach out with any questions!
