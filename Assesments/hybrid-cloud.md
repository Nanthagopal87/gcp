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

#

### 3. You need to migrate a standalone Java application running in an on-premises Linux virtual machine (VM) to Google Cloud in a cost-effective manner. You decide not to take the lift-and-shift approach, and instead you plan to modernize the application by converting it to a container.

How should you accomplish this task?

- A. Use Migrate for Anthos to migrate the VM to your Google Kubernetes Engine (GKE) cluster as a container.

- B. Export the VM as a raw disk and import it as an image. Create a Compute Engine instance from the imported image.

- C. Use Migrate for Compute Engine to migrate the VM to a Compute Engine instance, and use Cloud Build to convert it to a container.

- D. Use Jib to build a Docker image from your source code, and upload it to Artifact Registry. Deploy the application in a GKE cluster, and test the application.

### Ans: D

ncorrect Answers:

A. Use Migrate for Anthos to migrate the VM to your Google Kubernetes Engine (GKE) cluster as a container.

B. Export the VM as a raw disk and import it as an image. Create a Compute Engine instance from the imported image.

C. Use Migrate for Compute Engine to migrate the VM to a Compute Engine instance, and use Cloud Build to convert it to a container.

Option A, using Migrate for Anthos, would migrate the VM to GKE, but this is more of a lift-and-shift approach and doesn't necessarily involve modernizing the application.

Option B, exporting the VM as a raw disk and importing it as an image, doesn't involve containerization and is more related to replicating the VM in the cloud.

Option C, using Migrate for Compute Engine to migrate the VM to Compute Engine and then using Cloud Build, may lead to a containerized solution, but it's more complex than necessary for the given task.



Correct Answer:

D. Use Jib to build a Docker image from your source code, and upload it to Artifact Registry. Deploy the application in a GKE cluster, and test the application.

Option D, using Jib to build a Docker image from the source code, allows for a more modern approach by building a containerized image directly from the source code. It also includes deployment in GKE, which aligns with the goal of moving to a container-based architecture. Jib is a Maven/Gradle plugin specifically designed for building Java container images, making it a suitable choice for this Java application migration.

In the given scenario, where the goal is to modernize the application by converting it to a container rather than just lifting and shifting the VM, option D is the most appropriate approach.


Links:

https://cloud.google.com/blog/products/application-development/introducing-jib-build-java-docker-images-better

