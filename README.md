# on_demand_data_etl
Data project to build out a simple dashboard that is populated by near real-time bitcoin exchange data.

Project
For this project, the dashboard will pull bitcoin exchange data from CoinCap API. This will pull data every 5 minutes and load it into our warehouse.

Requirements:

1. Docker and Docker Compose v1.27.0 or later.
2. AWS account.
3. AWS CLI installed and configured.
4. git

ETL Code
The code to pull data from CoinCap API and load it into our warehouse is at exchange_data_etl.py. 

Test
Tests are crucial if you want to be confident about refactoring code, adding new features, and code correctness. 

Unit test: To test if individual functions are working as expected. We test get_utc_from_unix_time with the test_get_utc_from_unix_time function.
Integration test: To test if multiple systems work together as expected.

Scheduler
Now that we have the ETL script and tests setup. We need to schedule the ETL script to run every 5 minutes. Since this is a simple script we will go with cron instead of setting up a framework like Airflow or Dagster. The cron job is defined at scheduler/pull_bitcoin_exchange_info

Presentation
Now that we have the code and scheduler set up, we can add checks and formatting automation to ensure that we follow best practices.

Live Dashboard
We can spin up a dashboard locally using the following commands.

cd bitcoinMonitor
make up

Then visit http://localhost:3000 to log into your local Metabase instance. From the Metabase UI, you can add charts and dashboards. 

Deploy to Production
Now that you have your code working locally, it’s time to deploy to production. We will run our data pipeline and dashboards as containers on an EC2 instance. The first step is to start an EC2 ubuntu instance.
