### 1. Your company has created an application that uploads a report to a Cloud Storage bucket. When the report is uploaded to the bucket, you want to publish a message to a Cloud Pub/Sub topic. You want to implement a solution that will require only a small amount of effort to implement.

What should you do?

- A. Configure the Cloud Storage bucket to trigger Cloud Pub/Sub notifications when objects are modified.
- B. Create an App Engine application to receive the file; when it is received, publish a message to the Cloud Pub/Sub topic.
- C. Create a Cloud Function that is triggered by the Cloud Storage bucket. In the Cloud Function, publish a message to the Cloud Pub/Sub topic.
- D. Create an application deployed in a Google Kubernetes Engine cluster to receive the file; when it is received, publish a message to the Cloud Pub/Sub topic.

### Ans: A

Cloud Storage buckets can be configured to send notifications to a Cloud Pub/Sub topic when objects are added or modified in the bucket. This is simple to set up and meets your needs perfectly. Hence, Option A is the most straightforward and efficient way to achieve the desired behavior.

https://cloud.google.com/storage/docs/pubsub-notifications#other_notification_options

https://cloud.google.com/storage/docs/pubsub-notifications#overview

### 2. You are developing an application that reads credit card data from a Pub/Sub subscription. You have written code and completed unit testing. You need to test the
Pub/Sub integration before deploying to Google Cloud.

What should you do?

- A. Create a service to publish messages, and deploy the Pub/Sub emulator. Generate random content in the publishing service, and publish to the emulator.

- B. Create a service to publish messages to your application. Collect the messages from Pub/Sub in production, and replay them through the publishing service.

- C. Create a service to publish messages, and deploy the Pub/Sub emulator. Collect the messages from Pub/Sub in production, and publish them to the emulator.

- D. Create a service to publish messages, and deploy the Pub/Sub emulator. Publish a standard set of testing messages from the publishing service to the emulator.

### Ans: D

Provides a controlled testing environment. By using the emulator and publishing a standard set of testing messages, you can validate the integration and behavior of your application without relying on production data or creating dependencies on other services. So, this option is the most suitable approach for testing the Pub/Sub integration in a controlled and secure manne

https://cloud.google.com/pubsub/docs/emulator

### 3. Your team develops services that run on Google Cloud. You want to process messages sent to a Pub/Sub topic, and then store them. Each message must be processed exactly once to avoid duplication of data and any data conflicts. You need to use the cheapest and most simple solution.

What should you do?

- A. Process the messages with a Dataproc job, and write the output to storage.

- B. Process the messages with a Dataflow streaming pipeline using Apache Beam's PubSubIO package, and write the output to storage.

- C. Process the messages with a Cloud Function, and write the results to a BigQuery location where you can run a job to deduplicate the data.

- D. Retrieve the messages with a Dataflow streaming pipeline, store them in Cloud Bigtable, and use another Dataflow streaming pipeline to deduplicate messages.

### Ans: B

A. Process the messages with a Dataproc job, and write the output to storage.

Dataproc is primarily used for batch processing. If you need to process messages from a Pub/Sub topic in real time, Dataproc may not be the best choice.



C. Process the messages with a Cloud Function, and write the results to a BigQuery location where you can run a job to deduplicate the data.

Using Cloud Functions and then running a job to deduplicate the data in BigQuery adds complexity to the solution. Additionally, Cloud Functions may not guarantee exactly-once processing if not properly configured, leading to potential duplication.

D. Retrieve the messages with a Dataflow streaming pipeline, store them in Cloud Bigtable, and use another Dataflow streaming pipeline to deduplicate messages.

Retrieving the messages with a Dataflow streaming pipeline, storing them in Cloud Bigtable, and then using another Dataflow streaming pipeline to deduplicate messages would be overly complex and costly compared to using Dataflow with Apache Beam's PubSubIO package.


B. Process the messages with a Dataflow streaming pipeline using Apache Beam's PubSubIO package, and write the output to storage.

Option B provides a straightforward and cost-effective way to achieve exactly-once processing. Apache Beam's PubSubIO package is designed to work with Pub/Sub, and you can implement the required logic to ensure that each message is processed exactly once. Writing the output to storage as part of the same pipeline ensures a cohesive solution that meets your requirements.

https://cloud.google.com/dataflow/docs/concepts/streaming-with-cloud-pubsub




