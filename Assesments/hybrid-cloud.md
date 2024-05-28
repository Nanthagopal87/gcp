### 1. You have an on-premises application that authenticates to the Cloud Storage API using a user-managed service account with a user-managed key. The application connects to Cloud Storage using Private Google Access over a Dedicated Interconnect link. You discover that requests from the application to access objects in the Cloud Storage bucket are failing with a 403 Permission Denied error code.

What is the likely cause of this issue?

- A. The folder structure inside the bucket and object paths have changed.

- B. The permissions of the service account’s predefined role have changed.

- C. The service account key has been rotated but not updated on the application server.

- D. The Interconnect link from the on-premises data center to Google Cloud is experiencing a temporary outage.

### Ans: C

The error code "403 Permission Denied" typically indicates an authentication or authorization problem rather than a connectivity issue.

Among the provided options, the most likely cause of this error would be that the service account key has been rotated but not updated on the application server, leading to failed authentication attempts.

So Option C is the most typical scenario for a "403 Permission Denied" error, making it the most likely cause of the issue described.

Links:

[Troubleshooting 403 error messages](https://cloud.google.com/storage/docs/troubleshooting#troubleshooting-403)

### 2. You migrated some of your applications to Google Cloud. You are using a legacy monitoring platform deployed on-premises for both on-premises and cloud- deployed applications. You discover that your notification system is responding slowly to time-critical problems in the cloud applications.

What should you do?

- A. Replace your monitoring platform with Cloud Monitoring.

- B. Install the Cloud Monitoring agent on your Compute Engine instances.

- C. Migrate some traffic back to your old platform. Perform A/B testing on the two platforms concurrently.

- D. Use Cloud Logging and Cloud Monitoring to capture logs, monitor, and send alerts. Send them to your existing platform.

### Ans: D

Allows you to utilize Google Cloud's monitoring tools to capture the necessary logs and alerts while still integrating with your existing monitoring platform. This would enable faster response to time-critical problems without a complete overhaul of your existing monitoring system.

https://cloud.google.com/logging/docs/export

https://cloud.google.com/monitoring/api/v3/

