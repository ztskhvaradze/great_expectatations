# Great Expectations SQL Server Project

This project demonstrates how to use Great Expectations with SQL Server to create validation checks and documentation for your data using Expectation Suites, Checkpoints, and Data Docs. The example uses the AdventureWorks2012 sample database and validates the `Production.Location` table.

## Prerequisites

- Python 3.6 or higher
- Great Expectations library
- SQL Server instance with the AdventureWorks2012 sample database
- A valid SQL Server connection string to connect to the AdventureWorks2012 database

## Setup

1. Clone this repository:
git clone <repository_url>




2. Install the required Python dependencies:
   
* pip install great_expectations
  
* pip install sqlalchemy
  
* pip install pyodbc




4. Update the `connection_string` variable in the notebook to point to your own AdventureWorks2012 database.

## Usage

Run the Jupyter notebook, which demonstrates the following steps:

1. Initialize a Great Expectations DataContext for your project.

2. Set up and configure the SQL Server datasource.

3. Create a new empty Expectation Suite.

4. Create a BatchRequest to fetch data from the 'Production.Location' table in the AdventureWorks2012 database.

5. Validate the data using a built-in profiler to automatically generate an Expectation Suite.

6. Save the generated Expectation Suite to the DataContext.

7. Add custom Expectations to the Expectation Suite for more specific validation checks.

8. Validate the data against the custom Expectation Suite.

9. Generate and open Data Docs in your default web browser to browse your Expectation Suites and validation results.

10. Create a checkpoint configuration file for your data validation process.

11. Run the checkpoint using the Great Expectations CLI command or programmatically in your Python code.

The notebook demonstrates how to create Expectation Suites, validate data, generate Data Docs, and create Checkpoints using Great Expectations with SQL Server.

## Creating a Checkpoint

Checkpoints

1. Assuming you have successfully configured your datasource and created custom Expectation Suites, use the provided `checkpoint_creation.py` script to create a Checkpoint.
2. Configure the connection string in the script to match your database connection.
3. Set up a BatchRequest in the script to fetch data from the table you want to validate.
4. Use the `add_or_update_checkpoint()` method to create a Checkpoint with the appropriate name and referencing your custom Expectation Suite.
5. Run the Checkpoint using the `checkpoint.run()` method in your Python code.
6. The validation results will be stored in your DataContext and can be viewed in the Data Docs.
