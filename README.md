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
pip install -r requirements.txt




3. Update the `connection_string` variable in the notebook to point to your own AdventureWorks2012 database.

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

1. Create a checkpoint configuration file with a descriptive name, such as `location_table_checkpoint.yml`, in the `great_expectations/checkpoints/` folder of your project. The content of the file should look like this:

```yaml
name: location_table_checkpoint
config_version: 1.0
class_name: SimpleCheckpoint
validations:
  - batch_request:
        datasource_name: sql_server_datasoure
        data_connector_name: default_inferred_data_connector_name
        data_asset_name: Production.Location
    expectation_suite_name: Production.Product.basic_suite
This checkpoint configuration defines a checkpoint named location_table_checkpoint, and it uses the SimpleCheckpoint class to perform a single validation. The validation uses the Production.Product.basic_suite Expectation Suite and the sql_server_datasoure datasource.

Run the checkpoint using the Great Expectations CLI command:

bash


great_expectations checkpoint run location_table_checkpoint
This command will execute the data validation process defined by the checkpoint and generate the validation result. If any actions are associated with the checkpoint or the Expectation Suite (e.g., updating Data Docs), those actions will be executed as well.

To run the checkpoint programmatically from your Python code, use the context.run_checkpoint() method:

python


checkpoint_result = context.run_checkpoint(checkpoint_name="location_table_checkpoint")
print(checkpoint_result)
This example will run the checkpoint programmatically and print the validation result.

With a checkpoint in place, you can easily run the data validation process whenever needed, and integrate it into your data pipelines or other workflows for monitoring data quality more effectively.

Additional Notes
Remember to update the connection_string variable in the notebook to match your SQL Server configuration. You may need to adjust the table and column names used in the notebook if you want to use this project for validating different tables in the AdventureWorks2012 database or other database schemas.

To validate data in tables other than Production.Location, update the batch_request variable to fetch data from the desired table and adjust the expectations in the Expectation Suite accordingly.
