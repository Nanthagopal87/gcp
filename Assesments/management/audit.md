### 1. You manage your company's e-commerce platform's payment system, which runs on Google Cloud. Your company is required to retain user logs for 1 year for internal auditing purposes and for 3 years to meet compliance requirements. You need to store new user logs on Google Cloud to reduce on-premises storage usage and ensure that the logs are easily searchable.

What action should you take to minimize effort while ensuring that the logs are stored correctly?

- A. Store the logs in a Cloud Storage bucket with bucket lock turned on.

- B. Store the logs in a Cloud Storage bucket with a 3-year retention period.

- C. Store the logs in Cloud Logging as custom logs with a custom retention period.

- D. Store the logs in a Cloud Storage bucket with a 1-year retention period. After 1 year, move the logs to another bucket with a 2-year retention period.

### Ans: C

A. Store the logs in a Cloud Storage bucket with a bucket lock turned on.

B. Store the logs in a Cloud Storage bucket with a 3-year retention period.

D. Store the logs in a Cloud Storage bucket with a 1-year retention period. After 1 year, move the logs to another bucket with a 2-year retention period.

The requirements state that the logs should be easily searchable. This is not easily achieved in Cloud Storage, so that eliminates options A, B, and D.

C. Store the logs in Cloud Logging as custom logs with a custom retention period.

Cloud Logging retains logs according to retention rules that apply to the log bucket type where the logs are stored.

You can configure Cloud Logging to retain logs for a period ranging from 1 day to 3650(10 years) days. Custom retention rules apply to all the logs in a bucket, regardless of the log type or whether the log has been copied from another location.

https://cloud.google.com/logging/docs/buckets#custom-retention

https://cloud.google.com/logging/docs/routing/overview#logs-retention

https://cloud.google.com/logging/docs/audit/best-practices#custom-retention

https://cloud.google.com/logging/docs/central-log-storage

### 2. A governmental regulation was recently passed that affects your application. For compliance purposes, you are now required to send a duplicate of specific application logs from your application’s project to a project that is restricted to the security team.

What should you do?

- A. Create user-defined log buckets in the security team’s project. Configure a Cloud Logging sink to route your application’s logs to log buckets in the security team’s project.

- B. Create a job that copies the logs from the _Required log bucket into the security team’s log bucket in their project.

- C. Modify the _Default log bucket sink rules to reroute the logs into the security team’s log bucket.

- D. Create a job that copies the System Event logs from the _Required log bucket into the security team’s log bucket in their project.

### Ans: A

ncorrect Answers:

B. Create a job that copies the logs from the _Required log bucket into the security team’s log bucket in their project.

C. Modify the _Default log bucket sink rules to reroute the logs into the security team’s log bucket.

D. Create a job that copies the System Event logs from the _Required log bucket into the security team’s log bucket in their project.

Options B, C, and D are not the most effective solutions. They either involve manual jobs (B and D) that can be error-prone or they modify the default bucket (C) which might affect other logs not relevant to this regulation compliance.



Correct Answer:

A. Create user-defined log buckets in the security team’s project. Configure a Cloud Logging sink to route your application’s logs to log buckets in the security team’s project.

This solution provides a direct and automated solution for duplicating specific application logs and sending them to the security team's project. This method uses Cloud Logging's sink feature, a powerful tool for routing logs to other destinations, such as log buckets or Pub/Sub topics. By using a sink, you can ensure that the duplication of logs is performed in real-time and automatically, minimizing both manual intervention and the risk of errors.



Links:

https://cloud.google.com/architecture/security-log-analytics