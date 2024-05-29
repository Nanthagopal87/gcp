### 1. You recently developed an application. You need to call the Cloud Storage API from a Compute Engine instance that doesn't have a public IP address.

What should you do?

- A. Use Carrier Peering
- B. Use VPC Network Peering
- C. Use Shared VPC networks
- D. Use Private Google Access

### Ans: D
To access Google Cloud services like Cloud Storage API from a Compute Engine instance without a public IP address, you can use Private Google Access.

Private Google Access allows resources in your VPC network, without external IP addresses, to reach Google APIs and services using private IP addresses rather than the public internet.

https://cloud.google.com/vpc/docs/private-google-access

### 2. Your application is controlled by a managed instance group. You want to share a large read-only data set between all the instances in the managed instance group. You want to ensure that each instance can start quickly and can access the data set via its filesystem with very low latency. You also want to minimize the total cost of the solution.

What should you do?

- A. Move the data to a Cloud Storage bucket, and mount the bucket on the filesystem using Cloud Storage FUSE.
- B. Move the data to a Cloud Storage bucket, and copy the data to the boot disk of the instance via a startup script.
- C. Move the data to a Compute Engine persistent disk, and attach the disk in read-only mode to multiple Compute Engine virtual machine instances.
- D. Move the data to a Compute Engine persistent disk, take a snapshot, create multiple disks from the snapshot, and attach each disk to its own instance.

### Ans: C
meets all requirements: sharing a large read-only data set with low latency (since the persistent disk is attached directly to the VMs), quick start, and cost minimization (since you're using a single shared disk).

https://cloud.google.com/compute/docs/disks/add-persistent-disk#use-multi-instances


### 3. Your application performs well when tested locally, but it runs significantly slower after you deploy it to a Compute Engine instance. You need to diagnose the problem.

What should you do?

- A. File a ticket with Cloud Support indicating that the application performs faster locally.

- B. Use Cloud Debugger snapshots to look at a point-in-time execution of the application.

- C. Use Cloud Profiler to determine which functions within the application take the longest amount of time.

- D. Add logging commands to the application and use Cloud Logging to check where the latency problem occurs.

### Ans: C

Using Cloud Profiler, will allow you to analyze the application's performance, identifying which functions are taking the longest and potentially uncovering the root cause of the slowdown. This is a powerful tool specifically designed for performance optimization, making it the most suitable choice in this scenario.

https://cloud.google.com/profiler/docs

### 4. You are deploying your application on a Compute Engine instance that communicates with Cloud SQL. You will use Cloud SQL Proxy to allow your application to communicate to the database using the service account associated with the application's instance. You want to follow the Google-recommended best practice of providing minimum access for the role assigned to the service account.

What should you do?

- A. Assign the Project Editor role.
- B. Assign the Project Owner role.
- C. Assign the Cloud SQL Client role.
- D. Assign the Cloud SQL Editor role.

### Ans: C

This role provides the necessary permissions for the service account to connect to Cloud SQL instances but doesn't provide broader permissions that might expose you to unnecessary risk. That's why option C is the appropriate choice, adhering to the best practice of granting only the permissions that are necessary for the task at hand.

https://cloud.google.com/sql/docs/mysql/sql-proxy

https://cloud.google.com/sql/docs/mysql/roles-and-permissions#proxy-roles-permissions

### 5. Your team is building an application for a financial institution. The application's frontend runs on Compute Engine, and the data resides in Cloud SQL and one Cloud Storage bucket. The application will collect data containing PII, which will be stored in the Cloud SQL database and the Cloud Storage bucket. You need to secure the PII data.

What should you do?

- A.

1. Create the relevant firewall rules to allow only the frontend to communicate with the Cloud SQL database

2. Using IAM, allow only the frontend service account to access the Cloud Storage bucket

- B.

1. Create the relevant firewall rules to allow only the frontend to communicate with the Cloud SQL database

2. Enable private access to allow the frontend to access the Cloud Storage bucket privately

- C.

1. Configure a private IP address for Cloud SQL

2. Use VPC-SC to create a service perimeter

3. Add the Cloud SQL database and the Cloud Storage bucket to the same service perimeter

- D.

1. Configure a private IP address for Cloud SQL

2. Use VPC-SC to create a service perimeter

3. Add the Cloud SQL database and the Cloud Storage bucket to different service perimeters

### Ans: C

Option C would be the best choice for securing PII data in this scenario. Let's review why:

Configuring a private IP address for Cloud SQL: This step will make sure that the Cloud SQL instance is not exposed to the public Internet, thereby reducing the attack surface.

Using VPC Service Controls (VPC-SC) to create a service perimeter: VPC Service Controls enable you to define security boundaries around Google Cloud resources. By setting up a service perimeter, you are restricting the communication across the boundary, thus isolating the resources inside the perimeter from potential threats.

Adding the Cloud SQL database and the Cloud Storage bucket to the same service perimeter: Since both the Cloud SQL database and Cloud Storage bucket are used to store PII data, grouping them within the same service perimeter provides a consistent security policy and ensures that they can communicate with each other, while isolating them from unauthorized access.

https://cloud.google.com/vpc-service-controls/docs/service-perimeters

### 6. A. Configure the instances with a service account owned by project B. Add the service account as a Cloud Pub/Sub publisher to project A.

- A. Configure the instances with a service account owned by project B. Add the service account as a Cloud Pub/Sub publisher to project A.

- B. Configure the instances with a service account owned by project A. Add the service account as a publisher on the topic.

- C. Configure Application Default Credentials to use the private key of a service account owned by project B. Add the service account as a Cloud Pub/Sub publisher to project A.

- D. Configure Application Default Credentials to use the private key of a service account owned by project A. Add the service account as a publisher on the topic

### Ans: B

A. Configure the instances with a service account owned by project B. Add the service account as a Cloud Pub/Sub publisher to project A.

This option is incorrect because adding the service account as a Cloud Pub/Sub publisher to project A would not grant permissions to access the topic in project B.

C. Configure Application Default Credentials to use the private key of a service account owned by project B. Add the service account as a Cloud Pub/Sub publisher to project A.

This option is incorrect because, like option A, it involves adding the service account as a Cloud Pub/Sub publisher to project A, which doesn't grant the needed permissions for the topic in project B.

D. Configure Application Default Credentials to use the private key of a service account owned by project A. Add the service account as a publisher on the topic

This option is similar to option B but specifically mentions Application Default Credentials, which can be used but is not a necessary detail for the question. The essential part is configuring the service account with the appropriate permissions.



Correct Answer:

B. Configure the instances with a service account owned by project A. Add the service account as a publisher on the topic.

This option is the correct one. You would configure the instances in project A with a service account owned by project A and then grant that service account the necessary permissions (e.g., Publisher) on the specific topic in project B. By doing so, you are ensuring that the application hosted in project A has the permissions it needs to interact with the topic in project B.

Links:

https://cloud.google.com/pubsub/docs/access-control


### 7. Your application is composed of a set of loosely coupled services orchestrated by code executed on Compute Engine. You want your application to easily bring up new Compute Engine instances that find and use a specific version of a service.

How should this be configured?

- A. Define your service endpoint information as metadata that is retrieved at runtime and used to connect to the desired service.

- B. Define your service endpoint information as label data that is retrieved at runtime and used to connect to the desired service.

- C. Define your service endpoint information to be retrieved from an environment variable at runtime and used to connect to the desired service.

- D. Define your service to use a fixed hostname and port to connect to the desired service. Replace the service at the endpoint with your new version.

### Ans: A

B. Define your service endpoint information as label data that is retrieved at runtime and used to connect to the desired service.

Labels are typically used for organizing resources rather than for runtime configuration.

C. Define your service endpoint information to be retrieved from an environment variable at runtime and used to connect to the desired service.

Depending on environment variables can lead to tighter coupling and may not provide the desired flexibility for managing service versions.

D. Define your service to use a fixed hostname and port to connect to the desired service. Replace the service at the endpoint with your new version.

D. Using a fixed hostname and port might not provide the necessary flexibility to work with different versions of the service.



Correct Answer:

A. Define your service endpoint information as metadata that is retrieved at runtime and used to connect to the desired service.

Option A allows you to store the endpoint information as metadata, which can be retrieved by the Compute Engine instances at runtime. This method makes it possible to change the endpoint information without modifying the instances, thereby supporting loosely coupled services and easing the process of managing different versions of a service.

https://cloud.google.com/apis/design/glossary#api_service_endpoint

https://cloud.google.com/compute/docs/metadata/overview

https://cloud.google.com/service-infrastructure/docs/service-metadata/reference/rest#service-endpoint

### 8. You are deploying your applications on Compute Engine. One of your Compute Engine instances failed to launch.

What should you do? (Choose two options.)

- A. Determine whether your file system is corrupted.

- B. Access Compute Engine as a different SSH user.

- C. Troubleshoot firewall rules or routes on an instance.

- D. Check whether your instance boot disk is completely full.

- E. Check whether network traffic to or from your instance is being dropped.

### Ans: C & D

Incorrect Answers:

A. Determine whether your file system is corrupted.

B. Access Compute Engine as a different SSH user.

E. Check whether network traffic to or from your instance is being dropped.

Option A While filesystem corruption can be a cause of instance failure, it's less likely to be the immediate cause of a failed instance launch. Checking the filesystem integrity can be part of troubleshooting, but it's not as critical as ensuring sufficient disk space (Option D) or proper network connectivity (Option E) for the instance to launch.

Option B This option is unrelated to troubleshooting a failed instance launch. Accessing Compute Engine as a different SSH user doesn't address the underlying issue causing the instance failure.

Option E While network issues can indeed cause instance launch failures, troubleshooting firewall rules or routes (Option C) directly addresses potential network connectivity problems. Checking whether network traffic is being dropped (Option E) is essentially part of this troubleshooting process.

Correct Answer:

C. Troubleshoot firewall rules or routes on an instance.

D. Check whether your instance boot disk is completely full.

The most immediate and relevant steps to address a failed instance launch are to troubleshoot firewall rules or routes (Option C) and to check whether the instance boot disk is completely full (Option D). These actions focus on ensuring proper network connectivity and disk space, which are essential for a successful instance launch.

https://cloud.google.com/compute/docs/troubleshooting/vm-startup



Links:

https://cloud.google.com/compute/docs/troubleshooting/vm-startup
