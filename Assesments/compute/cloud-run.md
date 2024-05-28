### 1. You are supporting a business-critical application in production deployed on Cloud Run. The application is reporting HTTP 500 errors that are affecting the usability of the application. You want to be alerted when the number of errors exceeds 15% of the requests within a specific time window.

What should you do?

- A. Create a Cloud Function that consumes the Cloud Monitoring API. Use Cloud Scheduler to trigger the Cloud Function daily and alert you if the number of errors is above the defined threshold.
- B. Navigate to the Cloud Run page in the Google Cloud console, and select the service from the services list. Use the Metrics tab to visualize the number of errors for that revision, and refresh the page daily.
- C. Create an alerting policy in Cloud Monitoring that alerts you if the number of errors is above the defined threshold.
- D. Create a Cloud Function that consumes the Cloud Monitoring API. Use Cloud Composer to trigger the Cloud Function daily and alert you if the number of errors is above the defined threshold.

### Ans: C
This is the right approach because:

It allows for direct monitoring of metrics and setting thresholds.

It can send alerts based on the conditions specified without the need for manual checks.

It doesn't require the additional complexity of setting up Cloud Functions, Cloud Scheduler, or Cloud Composer.

https://cloud.google.com/monitoring/alerts/policies-in-api#metric-polices


### 2. Your team is developing a new application using a PostgreSQL database and Cloud Run. You are responsible for ensuring that all traffic is kept private on Google
Cloud. You want to use managed services and follow Google-recommended best practices. What should you do?

1. Enable Cloud SQL and Cloud Run in the same project.

2. Configure a private IP address for Cloud SQL. Enable private services access.

3. Create a Serverless VPC Access connector.

4. Configure Cloud Run to use the connector to connect to Cloud SQL.

Enable Cloud SQL and Cloud Run in the same project: By using Cloud SQL (a managed service), you don't need to manage PostgreSQL yourself. Keeping them in the same project simplifies networking and access management.

Configure a private IP address for Cloud SQL. Enable private services access: This ensures that the connection between Cloud SQL and Cloud Run is private and stays within Google's network.

Create a Serverless VPC Access connector: This allows Cloud Run to connect to your VPC network so that it can access the Cloud SQL instance privately.

Configure Cloud Run to use the connector to connect to Cloud SQL: This ensures that the connection from Cloud Run to Cloud SQL uses the private connection provided by the Serverless VPC Access connector.

Therefore, Option A aligns best with the goal of keeping traffic private using managed services and following Google-recommended best practices.

https://cloud.google.com/sql/docs/postgres/connect-run#configure

https://cloud.google.com/sql/docs/postgres/connect-run#private-ip

### 3. You are using Cloud Run to host a web application. You need to securely obtain the application project ID and region where the application is running and display this information to users. You want to use the most performant approach.

What should you do?

- A. Use HTTP requests to query the available metadata server at the http://metadata.google.internal/ endpoint with the Metadata-Flavor: Google header.

- B. In the Google Cloud console, navigate to the Project Dashboard and gather configuration details. Navigate to the Cloud Run “Variables & Secrets” tab, and add the desired environment variables in Key:Value format.

- C. In the Google Cloud console, navigate to the Project Dashboard and gather configuration details. Write the application configuration information to Cloud Run's in-memory container filesystem.

- D. Make an API call to the Cloud Asset Inventory API from the application and format the request to include instance metadata.

### Ans: A

A. Use HTTP requests to query the available metadata server at the http://metadata.google.internal/ endpoint with the Metadata-Flavor: Google header.

Provides a direct way to obtain metadata within a Cloud Run container. Querying the metadata server is a common pattern for obtaining runtime information about a service. This method is designed for this exact use case, making it the most performant approach among the options.

B. In the Google Cloud console, navigate to the Project Dashboard and gather configuration details. Navigate to the Cloud Run “Variables & Secrets” tab, and add the desired environment variables in Key:Value format.

Involves manually adding environment variables through the Google Cloud Console. This method is not dynamic and would require manual updates if the information changes.

C. In the Google Cloud console, navigate to the Project Dashboard and gather configuration details. Write the application configuration information to Cloud Run's in-memory container filesystem.

Is similar to option B but involves writing the information to the container's filesystem. This is also not a dynamic approach and requires manual updates.

D. Make an API call to the Cloud Asset Inventory API from the application and format the request to include instance metadata.

Involves making an API call to the Cloud Asset Inventory API, which could add unnecessary complexity and overhead, making it less performant compared to querying the metadata server directly.

https://cloud.google.com/run/docs/container-contract#metadata-server



