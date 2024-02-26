# fred_pcf

## Solution
 - Ive used redpanda which is a kafka compatible streaming client for simulating a producer
 - The kafka connect s3 sink is configured to use mini-io which is an s3 compatible storage backend used extensively for local testing.
 - The docker compose file comtaines the necessary parameters which the s3 sink requires to be able to save partitioned data to s3.
 - the entire solution can be run locally with no need to connect to any third party vendors.


## How to run locally
1. Run command ``` docker compose up -d```
2. Navigate to http://localhost:8080/topics
3. click the ```game-analytics``` topic and in the actions menu publish a message (you can copy a line of json from mock data.json file)
4. Open http://localhost:9001/login and use ```minioadmin``` as username and password
5. You should see the fred-pcf folder where the data is sotred partitioned by incoming date in the format ```"year=YYYY/month=MM/day=dd/hour=HH"``` format
6. each new message will automatically be stored to s3 , you can test with a few more publish message events. 