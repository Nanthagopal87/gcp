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

#

### 4. You have recently developed a new application and want to deploy it on Cloud Run without using a Dockerfile.

Considering your organization's requirement that all container images must be pushed to a centrally managed container repository, how should you build your container using Google Cloud services? (Choose two options.)


- A. Push your source code to Artifact Registry.

- B. Submit a Cloud Build job to push the image.

- C. Use the pack build command with pack CLI.

- D. Include the --source flag with the gcloud run deploy CLI command.

- E. Include the --platform=kubernetes flag with the gcloud run deploy CLI command.

### Ans: C & D

ncorrect Answers:

A. Push your source code to Artifact Registry.

B. Submit a Cloud Build job to push the image.

E. Include the --platform=kubernetes flag with the gcloud run deploy CLI command.

Option A: is incorrect because Artifact Registry is designed for container images, not source code.

Option B: is incorrect because only the built image needs to be deployed to Cloud Run. A "centrally managed container repository" could be located outside Google, so the build tool may not necessarily be Cloud Build.

Option: E: is irrelevant in this case, as Kubernetes (K8S) is not involved in the question.



Correct Answer:

C. Use the pack build command with pack CLI.

D. Include the --source flag with the gcloud run deploy CLI command.

Option C: Google Cloud supports buildpacks—an open-source technology that facilitates the rapid and effortless creation of secure, production-ready container images from source code, without needing a Dockerfile. https://cloud.google.com/blog/products/containers-kubernetes/google-cloud-now-supports-buildpacks

Option D: Deploying from source code is possible in Cloud Run. You can deploy new services and new revisions directly from source code using a single gcloud CLI command, gcloud run deploy, with the --source flag.

https://cloud.google.com/run/docs/deploying-source-code



Links:

https://cloud.google.com/run/docs/deploying-source-code

https://cloud.google.com/blog/products/containers-kubernetes/google-cloud-now-supports-buildpacks

### 5. Users are complaining that your Cloud Run-hosted website responds too slowly during traffic spikes.
You want to provide a better user experience during traffic peaks.
What should you do?

- A. Read application configuration and static data from the database on application startup.

- B. Package application configuration and static data into the application image during build time.

- C. Perform as much work as possible in the background after the response has been returned to the user.

- D. Ensure that timeout exceptions and errors cause the Cloud Run instance to exit quickly so a replacement instance can be started.

### Ans: B

ncorrect Answers:

A. Read application configuration and static data from the database on application startup.

Reading data from the database on every startup could actually add to the latency, especially during traffic spikes when new instances are likely to be started frequently.

C. Perform as much work as possible in the background after the response has been returned to the user.

While offloading background tasks can improve user-perceived performance, it doesn't specifically address the issue of slow response times during traffic spikes. Background tasks might even consume additional resources that could be used to handle incoming requests.

D. Ensure that timeout exceptions and errors cause the Cloud Run instance to exit quickly so a replacement instance can be started.

While quickly replacing failing instances is generally a good practice, this doesn't specifically address the issue of slow response times during high traffic. Additionally, constantly replacing instances could lead to additional overhead and further slow down response times.



Correct Answer:

B. Package application configuration and static data into the application image during build time.

By bundling configuration and static data into the application image, you reduce the need to fetch this data from external sources during runtime. This can lead to faster response times, particularly during traffic peaks when the system is under increased load.



Links:

https://cloud.google.com/blog/topics/developers-practitioners/3-ways-optimize-cloud-run-response-times
