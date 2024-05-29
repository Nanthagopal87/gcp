### 1. You want to notify on-call engineers about a service degradation in production while minimizing development time.

What should you do?

- A. Use Cloud Function to monitor resources and raise alerts.

- B. Use Cloud Pub/Sub to monitor resources and raise alerts.

- C. Use Cloud Error Reporting to capture errors and raise alerts.

- D. Use Cloud Monitoring to monitor resources and raise alerts.

### Ans: C

Would be the most appropriate choice here. It provides built-in functionalities for tracking various metrics, setting up conditions that trigger alerts, and notifying the necessary personnel.

Links:

https://cloud.google.com/error-reporting/docs/notifications

https://cloud.google.com/blog/products/gcp/drilling-down-into-stackdriver-service-monitoring

### 2. You are deploying your application to a Compute Engine virtual machine instance with the Cloud Monitoring Agent(formerly Stackdriver) installed. Your application is a unix process on the instance. You want to be alerted if the unix process has not run for at least 5 minutes. You are not able to change the application to generate metrics or logs.

Which alert condition should you configure?

- A. Uptime check

- B. Process health

- C. Metric absence

- D. Metric threshold

### Ans: B

ncorrect Answers:

A. Uptime check

This would be used to monitor the availability of a network endpoint, such as a web server, not a specific process on a machine.

C. Metric absence

This refers to the absence of data for a specific metric, not the absence of a process. While you might use this in more complex scenarios, it's not directly designed to monitor process health.

D. Metric threshold

This would allow you to set an alert based on a specific metric value crossing a certain threshold, but it's not designed to check if a specific process is running or not.



Correct Answer:

B. Process health

In the described scenario, you want to monitor a specific Unix process and be alerted if that process hasn't run for at least 5 minutes. Since you are monitoring the presence or absence of a process, the appropriate alert condition would be Process health.

The Cloud Monitoring Agent can monitor system and process metrics, and this type of alert would specifically track the health of the Unix process.



Links:

Behavior of metric-based alerting policies | Cloud Monitoring
https://cloud.google.com/monitoring/alerts/concepts-indepth


### 3. Your team recently deployed an application on Google Kubernetes Engine (GKE). You are monitoring your application and want to be alerted when the average memory consumption of your containers is under 20% or above 80%. How should you configure the alerts?

- A. Create a Cloud Function that consumes the Monitoring API. Create a schedule to trigger the Cloud Function hourly and alert you if the average memory consumption is outside the defined range.

- B. In Cloud Monitoring, create an alerting policy to notify you if the average memory consumption is outside the defined range.

- C. Create a Cloud Function that runs on a schedule, executes kubectl top on all the workloads on the cluster, and sends an email alert if the average memory consumption is outside the defined range.

- D. Write a script that pulls the memory consumption of the instance at the OS level and sends an email alert if the average memory consumption is outside the defined range.

### Ans: B

Incorrect Answers:

A. Create a Cloud Function that consumes the Monitoring API. Create a schedule to trigger the Cloud Function hourly and alert you if the average memory consumption is outside the defined range.

This option involves writing a Cloud Function to query the Monitoring API for memory usage metrics and scheduling it to run hourly. While this approach allows for custom logic to assess memory consumption, it can be more complex to set up and maintain. Additionally, running it hourly may not provide real-time monitoring, potentially delaying alerts.

C. Create a Cloud Function that runs on a schedule, executes kubectl top on all the workloads on the cluster, and sends an email alert if the average memory consumption is outside the defined range.

Similar to Option A, this option also uses a Cloud Function, but instead of using the Monitoring API, it executes kubectl top to gather memory usage data. This approach is less efficient and more complex than directly using Cloud Monitoring. Additionally, executing kubectl commands from a Cloud Function involves additional setup for authentication and permissions.

D. Write a script that pulls the memory consumption of the instance at the OS level and sends an email alert if the average memory consumption is outside the defined range.

This approach requires writing a custom script to monitor memory usage at the OS level, which is a more manual and less integrated solution. It may not accurately reflect container-level memory consumption, especially in a Kubernetes environment where workloads are dynamically managed across multiple nodes.

Correct answer:

B. In Cloud Monitoring, create an alerting policy to notify you if the average memory consumption is outside the defined range.

Cloud Monitoring, formerly Stackdriver, offers comprehensive monitoring capabilities for GKE and other Google Cloud services. Creating an alerting policy directly in Cloud Monitoring is a straightforward and effective way to track memory consumption. This approach benefits from easy setup, integration with Google Cloud services, and real-time alerting capabilities.

Links:

https://cloud.google.com/monitoring