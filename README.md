# BU OMDS MOD 4: Data Management at Scale

### Course and Homework Overview
This course empowers students with the skills to design and implement data processing workflows essential for informed decision-making within large-scale systems. Throughout the semester, students will navigate the full data science lifecycle—from question formulation to data collection, wrangling, analysis, and visualization. The course applies tools and techniques for data collection, integration, and interpretation across relational (SQL), non-relational (NoSQL), and Big Data paradigms, enabling students to build, optimize, and maintain data pipelines and decision-making algorithms. When you have finished this course and related assignments, you too can join the illustrious group of BU Data Warriors!

### Core Topics Covered
- Consolidation, synchronization, and summarization of multiple data streams
- Data maintenance and availability
- Optimization and analytics for large-scale, static, and streaming data
- Interactive visualization platforms for online and offline data presentation
- Real-world data applications in equity, sustainability, health, and civic technology through collaborations with CDS Impact Labs and co-Labs

### Course Objectives
Upon completion, students will gain hands-on experience and expertise in:
- **Data Processing Pipelines**: Design and implementation for efficient data flows
- **Complex Data Modeling**: Architecting for various data requirements
- **Distributed Workloads**: System support for processing large data volumes
- **Relational Query Optimization**: Improving SQL query performance
- **Data Stream Processing**: Understanding dataflow programming and stream processing
- **Modern Data Processing Systems**: Exposure to Hadoop, Apache Spark, Databricks, and similar systems
- **Collaborative Projects**: Practical exposure to project management tools and software engineering best practices

---

## Getting Started with Assignments

### Prerequisites
Ensure you have a Microsoft Azure student account. Instructions for setup of environment resources will be provided in individual homework assignments.

### The following instructions are for setting up your Azure environment homework resources to ensure proper service deployment and minimum expenditures. Similar to many organizations, each Azure service option has an SKU assigned with availability dictated by capacity and resources within each Azure region. For each asssignment where resources do not have manual instructions for deployment, you will use the following instructions and specify each homework assignment in the details of the deployment. If you run into trouble, please work with your Learning Facilitator for assistance. These instructions assume you have created your Azure account, and deployed the necessary resources in Homework 1a. If not, please head over there first before continuing.

1. **Sign In**: Log into the [Azure Portal](https://portal.azure.com) with your student account.
2. **Access Cloud Shell**: 
   - Use the **[>_]** button next to the search bar to open a new Cloud Shell.
   - Select **PowerShell** as the environment, creating storage if prompted. Choose the "Azure for Students" subscription.
   - You can resize the Cloud Shell pane or minimize it using the controls on the top right.

    > **Note**: You may use **Bash** or **PowerShell** by changing the environment in the Cloud Shell pane's dropdown.

3. **Clone the Repository**:
   - In the PowerShell pane, enter the following command to clone the course repository:
   ```bash
   git clone https://github.com/cseferlis/OMDSMod4.git
   ```
4. **Navigate to the Homework Directory**:
   - After cloning, switch to the main folder for the exercises:
   ```bash
   cd OMDSMod4
   ```
5. **Running Setup Scripts**:
   - Navigate to the specific `homework` directory you’re working on and run the setup script to generate necessary files:
   ```bash
   bash ./formTemplate.sh
   ```

6. **Deploying Resources in Azure**:

This command will use a predefined template to create resources as required for the assignment.

   - Use the following command, replacing placeholders marked with <resource-group-name>, <path-to-template.json>, and <path-to-parameters.json> using the actual resource group name, template, and parameter file paths for your environment:
   ```bash
   az deployment group create --resource-group <resource-group-name> --template-file <path-to-template.json> --parameters @<path-to-parameters.json>
   ```
   Example:
   ```bash
   az deployment group create --resource-group OMDSMod4 --template-file ./homework1/azuredeploy.json --parameters @./homework1/azuredeploy.parameters.json
   ```


---

## Additional Resources
For further guidance on using Azure, refer to:
- [Azure Cloud Shell Documentation](https://docs.microsoft.com/azure/cloud-shell/overview)
- [Azure for Students Documentation](https://azure.microsoft.com/en-us/free/students/)

---

## Troubleshooting
- **Cloud Shell Environment**: Ensure you're using the correct environment (PowerShell or Bash).
- **Resource Group Names**: Use unique names for resource groups to avoid conflicts.
- **Azure Subscription**: Verify you are using the "Azure for Students" subscription to utilize free resources.

For any questions or issues, please reach out through the course discussion platform or contact your instructor directly.

---

Happy learning!