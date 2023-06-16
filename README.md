# Pipeline for Operations and X Data

This repository contains a data engineering pipeline script written in Python that handles operations and sales data. The script performs data ingestion, extraction, transformation, and loading into an Azure SQL database. The pipeline consists of the following steps:

## Prerequisites

Before running the pipeline, ensure that you have the following:

- Python installed on your machine
- Access to the data source file, `database_sales.xls`
- Azure SQL Server details, including the server name, database name, username, and password
- Required Python libraries installed (pandas, datetime, numpy, pyodbc, sqlalchemy)

## Pipeline Steps

1. Data Ingestion: Specify the path to the Excel file, `database_sales.xls`, containing the operations and sales data.

2. Data Extraction: Read the Excel file and extract each sheet corresponding to a specific year into separate DataFrames. The script iterates over the years, converts the year to a string, and uses the `pd.read_excel` function to read each sheet.

3. Data Transformation: Clean and organize the data to prepare it for further analysis. This step involves several transformations, such as adding headers, converting column names to snake_case, removing unnecessary columns, handling null values, and setting a minimum threshold for non-null values in rows.

4. Data Loading - Local: Save the transformed data as a CSV file named `dados.csv` in the root directory of the project. This file serves as an intermediate storage before uploading the data to Azure SQL.

5. Data Loading - Azure SQL: Connect to the Azure SQL database using the provided server, database, username, and password. Create an SQLAlchemy engine and upload the CSV data to the specified table in the database. The existing table is truncated before inserting the data to remove any previous records.

## Usage

To run the pipeline, follow these steps:

1. Set the necessary configurations in the script:
   - Set the `file_path` variable with the correct path to the `database_sales.xls` file.
   - Update the Azure SQL server details: `server`, `database`, `username`, `password`, and `table_name` variables.

2. Make sure you have the required Python libraries installed.

3. Execute the script: Run the script in a Python environment. Ensure you have the necessary access rights to read the Excel file and connect to Azure SQL.

4. Monitor the execution: The script will display logs and progress messages in the console. Check for any errors during data extraction, transformation, and loading.

5. Verify the results: Once the script completes successfully, check the Azure SQL database to ensure that the transformed data has been loaded into the specified table.

## Note

For security purposes, sensitive information such as connection strings and credentials has been omitted from this public script. Make sure to replace the placeholders in the script (`your_server_name`, `your_database_name`, `your_username`, `your_password`) with your actual Azure SQL Server details.

Please note that the data and script have been allowed and approved by the company to be posted on GitHub.

## License

This project is licensed under the [MIT License](LICENSE).

Feel free to customize and extend the pipeline to suit your specific requirements.
