### 1. You recently developed a new service on Cloud Run. The new service authenticates using a custom service, and then writes transactional information to a Cloud Spanner database. You need to verify that your application can support up to 5,000 read transactions and 1,000 write transactions per second while identifying any bottlenecks that may occur. Your test infrastructure must also be able to autoscale.

What should you do?

- A. Build a test harness to generate requests and deploy it to Cloud Run. Analyze the VPC Flow Logs using Cloud Logging.

- B. Create a Google Kubernetes Engine cluster running the Locust or JMeter images to dynamically generate load tests. Analyze the results using Cloud Trace.

- C. Create a Cloud Task to generate a test load. Use Cloud Scheduler to run 60,000 Cloud Task transactions per minute for 10 minutes. Analyze the results using Cloud Monitoring.

- D. Create a Compute Engine instance that uses a LAMP stack image from the Marketplace, and use Apache Bench to generate load tests against the service. Analyze the results using Cloud Trace.

### Ans: B

Incorrect Answers:

A. Build a test harness to generate requests and deploy it to Cloud Run. Analyze the VPC Flow Logs using Cloud Logging.

Deploying a test harness to Cloud Run would not be an ideal approach for load testing, and VPC Flow Logs are more suited to network monitoring rather than application performance analysis.

C. Create a Cloud Task to generate a test load. Use Cloud Scheduler to run 60,000 Cloud Task transactions per minute for 10 minutes. Analyze the results using Cloud Monitoring.

Using Cloud Task and Cloud Scheduler might not be flexible enough to simulate the required number of read and write transactions per second, especially if the load needs to be varied dynamically to test different scenarios.

D. Create a Compute Engine instance that uses a LAMP stack image from the Marketplace, and use Apache Bench to generate load tests against the service. Analyze the results using Cloud Trace.

A single Compute Engine instance using Apache Bench might not be able to generate enough load to reach the required number of transactions per second. Additionally, the LAMP stack image from the Marketplace is unrelated to the requirements of testing a Cloud Run service.



Correct Answer:

B. Create a Google Kubernetes Engine cluster running the Locust or JMeter images to dynamically generate load tests. Analyze the results using Cloud Trace.

To verify that your application can support up to 5,000 read and 1,000 write transactions per second, and to identify any bottlenecks that may occur, you can use a load testing tool such as Locust or JMeter to generate load tests on your Cloud Run service. These tools allow you to simulate a high number of concurrent requests and help you determine the maximum number of requests your service can handle.

You can run the load testing tool on a Google Kubernetes Engine (GKE) cluster, which will provide the autoscaling feature. This way, you can manage the high number of requests, and use Cloud Trace to analyze the results. This analysis will give you insights into performance and help you identify any bottlenecks.



Links:

https://cloud.google.com/architecture/distributed-load-testing-using-gke