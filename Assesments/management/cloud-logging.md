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