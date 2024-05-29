### 1. You are deploying your application to a Compute Engine virtual machine instance. Your application is configured to write its log files to disk. You want to view the logs in Cloud Logging without changing the application code.

What should you do?

- A. Install the Cloud Logging Agent and configure it to send the application logs.

- B. Use a Cloud Logging Library to log directly from the application to Cloud Logging.

- C. Provide the log file folder path in the metadata of the instance to configure it to send the application logs.

- D. Change the application to log to /var/log so that its logs are automatically sent to Cloud Logging.

### Ans: A

The agent can be configured to collect logs from various locations on the system, including custom log files produced by your application, and send them to Cloud Logging. Therefore, the correct option is A, where you would install and configure the Logging Agent to send the desired logs to Cloud Logging.

Links:

https://cloud.google.com/logging/docs/agent/logging/installation

### 2. You want to use the Cloud Logging Agent(formerly Stackdriver) to send an application's log file to Cloud Logging from a Compute Engine virtual machine instance.
After installing the Cloud Logging Agent, what should you do first?

- A. Enable the Error Reporting API on the project.

- B. Grant the instance full access to all Cloud APIs.

- C. Configure the application log file as a custom source.

- D. Create a Cloud Logs Export Sink with a filter that matches the application's log entries.

### Ans: C

Incorrect Answers:

A. Enable the Error Reporting API on the project.

This might be useful in some contexts but is not the immediate next step after installing the logging agent for sending logs to Cloud Logging(formerly Stackdriver).

B. Grant the instance full access to all Cloud APIs.

Granting full access to all Cloud APIs is excessive and not required for sending logs to Cloud Logging. Specific permissions related to logging would be needed, but typically these are managed by the roles and permissions assigned to the service account associated with the instance.

D. Create a Cloud Logs Export Sink with a filter that matches the application's log entries.

Exporting logs using sinks is a way to route logs to different destinations (such as BigQuery, Pub/Sub, etc.) and is not related to the task of setting up the agent to collect logs from a specific application log file.



Correct Answer:

C. Configure the application log file as a custom source.

This is the correct next step. By configuring the log file as a custom source, the agent will know where to look for the logs and how to process them. Therefore, option C is the most appropriate step to take after installing the Cloud Logging Agent.



Links:

https://cloud.google.com/logging/docs/agent/configuration

https://cloud.google.com/logging/docs/agent/configuration#streaming_logs_from_additional_inputs