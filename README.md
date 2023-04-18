# WK-8-Data-Pipelines-with-Neo4j
This repo contains project files for Data Pipelines with Neo4j Project


# Data Pipeline for Extracting, Transforming, and Loading Neo4j Data into Postgres
This data pipeline extracts customer subscription data from a Neo4j graph database, transforms it using Pandas, and loads it into a Postgres database.

## Prerequisites
* Access to a Neo4j database containing customer subscription data
* Python 3.x
* Required Python libraries: neo4j, pandas, psycopg2
## Setup
1. Install the required Python libraries using pip install -r requirements.txt
2. Set up your Neo4j connection details in the neo4j_uri, neo4j_user, and neo4j_password variables in etl.py.
3. Set up your Postgres connection details in the host, database, user, and password parameters in the psycopg2.connect() method call in the load_data() function in etl.py.
## Data Schema
The extracted data contains information about customer subscriptions to various services, including the customer ID, subscription ID, service ID, start date, end date, and price. The transformed data adds a new column for the duration of the subscription in days.

The final data schema in the Postgres database is as follows:

| Column Name  | Data Type | Description                                        |
|--------------|-----------|----------------------------------------------------|
| customer_id  | TEXT      | The ID of the customer who subscribed to the service |
| start_date   | DATE      | The start date of the customer's subscription      |
| end_date     | DATE      | The end date of the customer's subscription        |
| price        | FLOAT     | The price of the subscription                      |
| service_id   | TEXT      | The ID of the service subscribed to                |
| service_name | TEXT      | The name of the service subscribed to              |
| duration_days| INT       | The duration of the customer's subscription in days|

## Transformations
The *transform_data()* function performs the following transformations on the extracted data:

Converts the *start_date* and *end_date columns* to datetime format
Removes rows where *start_date* or *end_dat*e is missing
Drops all NaN values
Adds a new column for the duration of the subscription in days
## How to Run
To run the data pipeline, simply execute the .py file using Python:

The program will extract data from Neo4j, transform it, and load it into the Postgres database.

The program will log a success message if the data is successfully loaded into Postgres. If there is an error during any of the steps, an error message will be logged.

## Conclusion
This data pipeline provides a simple and efficient method for extracting, transforming, and loading customer subscription data from a Neo4j graph database into a Postgres database. The extracted data can be used for further analysis and reporting.
