### 1. Your company has a data warehouse that keeps your application information in BigQuery. The BigQuery data warehouse keeps 2 PBs of user data. Recently, your company expanded your user base to include EU users and needs to comply with these requirements:

Your company must be able to delete all user account information upon user request.

All EU user data must be stored in a single region specifically for EU users.

Which two actions should you take? (Choose two options)

- A. Use BigQuery federated queries to query data from Cloud Storage.

- B. Create a dataset in the EU region that will keep information about EU users only.

- C. Create a Cloud Storage bucket in the EU region to store information for EU users only.

- D. Re-upload your data using a Cloud Dataflow pipeline by filtering your user records out.

- E. Use DML statements in BigQuery to update/delete user records based on their requests.

### Ans: B & E

Option B. By creating a separate dataset in the EU region, you can store information about EU users in a specific region as required. This will satisfy the compliance requirement of storing all EU user data in a single region.

Option E. Utilizing Data Manipulation Language (DML) statements in BigQuery allows you to update or delete specific user records based on user requests. This enables you to comply with the requirement to delete all user account information upon user request.

Links:

https://cloud.google.com/bigquery/docs/reference/standard-sql/data-manipulation-language

https://cloud.google.com/architecture/bigquery-data-warehouse

### 2. Your analytics system executes queries against a BigQuery dataset. The SQL query is executed in batch and passes the contents of a SQL file to the BigQuery CLI. Then it redirects the BigQuery CLI output to another process. However, you are getting a permission error from the BigQuery CLI when the queries are executed.
You want to resolve the issue.

What should you do?

- A. Grant the service account BigQuery Data Viewer and BigQuery Job User roles.

- B. Grant the service account BigQuery Data Editor and BigQuery Data Viewer roles.

- C. Create a view in BigQuery from the SQL query and SELECT* from the view in the CLI.

- D. Create a new dataset in BigQuery, and copy the source table to the new dataset Query the new dataset and table from the CLI.

### Ans: A

B. Grant the service account BigQuery Data Editor and BigQuery Data Viewer roles.

The BigQuery Data Editor role would grant permissions to modify the data, not just view it, which might be unnecessary for executing queries. The permissions in this option might be too permissive for what is needed.

C. Create a view in BigQuery from the SQL query and SELECT* from the view in the CLI.

Creating a view from the SQL query would not resolve the permission issue, as the service account would still need the proper permissions to access the data and execute queries.

D. Create a new dataset in BigQuery, and copy the source table to the new dataset Query the new dataset and table from the CLI.

Copying the source table to a new dataset would not necessarily resolve the permission issue. You would still need to ensure that the service account has the appropriate permissions on the new dataset and table.

Correct Answer:

A. Grant the service account BigQuery Data Viewer and BigQuery Job User roles.

Option A is the correct choice for this scenario. By granting the service account the BigQuery Data Viewer role, you provide read access to the dataset, allowing the service account to view the data. The BigQuery Job User role allows the service account to create and run jobs, including queries, in BigQuery.

Links:

https://cloud.google.com/bigquery/docs/access-control#bigquery


### 2. You have an HTTP Cloud Function that is called via POST. Each submission's request body has a flat, unnested JSON structure containing numeric and text data. After the Cloud Function completes, the collected data should be immediately available for ongoing and complex analytics by many users in parallel.

How should you persist the submissions?

- A. Directly persist each POST request's JSON data into Datastore.

- B. Transform the POST request's JSON data, and stream it into BigQuery.

- C. Transform the POST request's JSON data, and store it in a regional Cloud SQL cluster.

- D. Persist each POST request's JSON data as an individual file within Cloud Storage, with the file name containing the request identifier.

### Ans: B

Incorrect Answers:

A. Directly persist each POST request's JSON data into Datastore.

Directly persist each POST request's JSON data into Datastore. Datastore is a NoSQL document database that can be used to store structured data, but it's not designed to handle the high volume of data that you need to analyze in near real-time. And it would require additional processing to be available for analysis.

C. Transform the POST request's JSON data, and store it in a regional Cloud SQL cluster.

Cloud SQL could handle the persistence of the data but might not be as efficient as BigQuery for complex analytics with many parallel users.

D. Persist each POST request's JSON data as an individual file within Cloud Storage, with the file name containing the request identifier.

Storing each POST request's JSON data as an individual file within Cloud Storage is inefficient for immediate and complex analytics.



Correct Answer:

B. Transform the POST request's JSON data, and stream it into BigQuery.

BigQuery is a highly scalable data warehouse that is well suited for handling large amounts of data and complex analytics in near real-time. By streaming the JSON data from your Cloud Function directly into BigQuery, you can make the collected data immediately available for analytics by many users in parallel. BigQuery support various data types including JSON, so you can store your request body without any transformation



Links:

https://cloud.google.com/bigquery/docs/streaming-data-into-bigquery


### 3. Your company has a BigQuery dataset named “Master”, which contains information about employee travel and expenses, organized by employee department. Since employees should only be able to view information for their respective departments, you want to apply a security framework to enforce this requirement using the minimum number of steps.

What should you do?

- A.

- Create a separate dataset for each department.

- Create a view with an appropriate WHERE clause to select records from a particular dataset for the specific department.

- Authorize this view to access records from your Master dataset.

- Give employees the permission to this department-specific dataset.

- B.

- Create a separate dataset for each department.

- Create a data pipeline for each department to copy appropriate information from the Master dataset to the specific dataset for the department.

- Give employees the permission to this department-specific dataset.

- C.

- Create a dataset named Master dataset.

- Create a separate view for each department in the Master dataset.

- Give employees access to the specific view for their department.

- D.

- Create a dataset named Master dataset.

- Create a separate table for each department in the Master dataset.

- Give employees access to the specific table for their department.


### Ans: C

C.

Create a dataset named Master dataset.

Create a separate view for each department in the Master dataset.

Give employees access to the specific view for their department.

This approach creates views within the existing "Master" dataset, tailoring access to specific departmental needs. It's likely the most straightforward to implement and manage, offering a good balance between security and ease of use and has a minimum number of steps.



Links:

https://cloud.google.com/bigquery/docs/share-access-views