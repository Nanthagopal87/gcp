### 1. You noticed that your application was forcefully shut down during a Deployment update in Google Kubernetes Engine. Your application didn’t close the database connection before it was terminated. You want to update your application to make sure that it completes a graceful shutdown.

What should you do?

- A. Update your code to process a received SIGTERM signal to gracefully disconnect from the database.
- B. Configure a PodDisruptionBudget to prevent the Pod from being forcefully shut down.
- C. Increase the terminationGracePeriodSeconds for your application.
- D. Configure a PreStop hook to shut down your application.

### Ans: A
https://cloud.google.com/blog/products/containers-kubernetes/kubernetes-best-practices-terminating-with-grace

### 2. You are a developer at a large organization. You have an application written in Go running in a production Google Kubernetes Engine (GKE) cluster. You need to add a new feature that requires access to BigQuery. You want to grant BigQuery access to your GKE cluster following Google-recommended best practices.

What should you do?

- A. Create a Google service account with BigQuery access. Add the JSON key to Secret Manager, and use the Go client library to access the JSON key.
- B. Create a Google service account with BigQuery access. Add the Google service account JSON key as a Kubernetes secret, and configure the application to use this secret.
- C. Create a Google service account with BigQuery access. Add the Google service account JSON key to Secret Manager, and use an init container to access the secret for the application to use.
- D. Create a Google service account and a Kubernetes service account. Configure Workload Identity on the GKE cluster, and reference the Kubernetes service account on the application Deployment

### Ans: D

The recommended way to authenticate applications running on Google Kubernetes Engine (GKE) that interact with other Google Cloud services (such as BigQuery) is to use Workload Identity. Workload Identity allows you to bind Kubernetes service accounts to Google service accounts, without the need to handle and manage individual keys.

Option D, "Create a Google service account and a Kubernetes service account. Configure Workload Identity on the GKE cluster, and reference the Kubernetes service account on the application Deployment," aligns with this best practice.

https://cloud.google.com/kubernetes-engine/docs/quickstarts/deploy-app-container-image#deploying_to_gke


### 3. Your team has created an application that is hosted on a Google Kubernetes Engine (GKE) cluster. You need to connect the application to a legacy REST service that is deployed in two GKE clusters in two different regions. You want to connect your application to the target service in a way that is resilient. You also want to be able to run health checks on the legacy service on a separate port.

How should you set up the connection? (Choose two options)

- A. Use Traffic Director with a sidecar proxy to connect the application to the service.
- B. Use a proxyless Traffic Director configuration to connect the application to the service.
- C. Configure the legacy service's firewall to allow health checks originating from the proxy.
- D. Configure the legacy service's firewall to allow health checks originating from the application.
- E. Configure the legacy service's firewall to allow health checks originating from the Traffic Director control plane.

### Ans: A & C

A. Use Traffic Director with a sidecar proxy to connect the application to the service.

This is a reasonable choice for connecting GKE applications across regions, as Traffic Director with sidecar proxies can provide load balancing and resilience. Traffic Director is designed to manage traffic for microservices and works well with sidecar proxies like Envoy.

C. Configure the legacy service's firewall to allow health checks originating from the proxy.

If you're using Traffic Director with sidecar proxies, the health checks will likely originate from the proxies themselves, so you'll need to allow this in the firewall rules for the legacy service.

https://cloud.google.com/traffic-director/docs/advanced-setup#routing-rule-maps

https://cloud.google.com/traffic-director/docs/advanced-setup

https://cloud.google.com/load-balancing/docs/health-check-concepts

### 4. You are developing an application that consists of several microservices running in a Google Kubernetes Engine cluster. One microservice needs to connect to a third-party database running on-premises. You need to store credentials to the database and ensure that these credentials can be rotated while following security best practices.

What should you do?

- A. Store the credentials in a sidecar container proxy, and use it to connect to the third-party database.

- B. Store the credentials as a Kubernetes Secret, and use the Cloud Key Management Service plugin to handle encryption and decryption.

- C. Store the credentials in an encrypted volume mount, and associate a Persistent Volume Claim with the client Pod.

- D. Configure a service mesh to allow or restrict traffic from the Pods in your microservice to the database.

### Ans: B

Kubernetes Secrets allow you to store and manage sensitive information.

By using Google Cloud's Key Management Service (KMS) with Kubernetes, you can ensure that the secrets are encrypted both in transit and at rest. The KMS provides cryptographic keys for your services to use, and integrates seamlessly with GKE for this exact use case.

Thus, Option B is the best choice for the given scenario.

https://cloud.google.com/kubernetes-engine/docs/how-to/encrypting-secrets


### 5. You plan to deploy a new application revision with a Deployment resource to Google Kubernetes Engine (GKE) in production. The container might not work correctly. You want to minimize risk in case there are issues after deploying the revision. You want to follow Google-recommended best practices.

What should you do?

- A. Perform a rolling update with a PodDisruptionBudget of 80%.

- B. Perform a rolling update with a HorizontalPodAutoscaler scale-down policy value of 0.

- C. Convert the Deployment to a StatefulSet, and perform a rolling update with a PodDisruptionBudget of 80%.

- D. Convert the Deployment to a StatefulSet, and perform a rolling update with a HorizontalPodAutoscaler scale-down policy value of 0.

### Ans: A

A rolling update ensures that only a certain percentage of Pods are taken down at a time, allowing the system to maintain availability. By using a PodDisruptionBudget, you can control the level of disruption and minimize risk.

This approach allows for gradual updates, maintaining 80% of the desired replicas. A PodDisruptionBudget (PDB) limits the number of concurrently disrupted Pods during voluntary disruptions. This option helps maintain availability during updates, which aligns with the goal of minimizing risk.

https://kubernetes.io/docs/tutorials/kubernetes-basics/update/update-intro/

https://cloud.google.com/blog/products/containers-kubernetes/ensuring-reliability-and-uptime-for-your-gke-cluster


### 6. You are planning to deploy hundreds of microservices in your Google Kubernetes Engine (GKE) cluster. How should you secure communication between the microservices on GKE using a managed service?

- A. Use global HTTP(S) Load Balancing with managed SSL certificates to protect your services
- B. Deploy open source Istio in your GKE cluster, and enable mTLS in your Service Mesh
- C. Install cert-manager on GKE to automatically renew the SSL certificates.

- D. Install Anthos Service Mesh, and enable mTLS in your Service Mesh.

### Ans: D

A. Use global HTTP(S) Load Balancing with managed SSL certificates to protect your services

Global HTTP(S) Load Balancing with managed SSL certificates is designed to handle external traffic, not internal communication between microservices in a cluster.

B. Deploy open source Istio in your GKE cluster, and enable mTLS in your Service Mesh

Deploying open-source Istio and enabling mTLS (mutual Transport Layer Security) would be a way to secure the communication between services. However, this option requires you to manage Istio yourself, which may not be ideal when you are specifically looking for a managed service.

C. Install cert-manager on GKE to automatically renew the SSL certificates.

Cert-manager on GKE is focused on automating the management and issuance of TLS certificates but doesn't provide a comprehensive solution for securing communication between microservices.



Correct Answer:

D. Install Anthos Service Mesh, and enable mTLS in your Service Mesh.

Installing Anthos Service Mesh and enabling mTLS in your Service Mesh provides a managed solution for securing communication between your microservices within the GKE cluster. This not only takes care of encrypting the traffic but also simplifies identity verification between services, in line with best practices for microservices communication.

Thus, option D is the best choice for a fully managed approach to securing microservices communication in a GKE cluster.

Links:

https://cloud.google.com/architecture/service-meshes-in-microservices-architecture#security_2

https://cloud.google.com/service-mesh/docs/overview#security_benefits

### 7. Your team develops stateless services that run on Google Kubernetes Engine (GKE). You need to deploy a new service that will only be accessed by other services running in the GKE cluster. The service will need to scale as quickly as possible to respond to changing load.

What should you do?

- A. Use a Vertical Pod Autoscaler to scale the containers, and expose them via a ClusterIP Service.

- B. Use a Vertical Pod Autoscaler to scale the containers, and expose them via a NodePort Service.

- C. Use a Horizontal Pod Autoscaler to scale the containers, and expose them via a ClusterIP Service.

- D. Use a Horizontal Pod Autoscaler to scale the containers, and expose them via a NodePort Service.

### Ans: C

A. Use a Vertical Pod Autoscaler to scale the containers, and expose them via a ClusterIP Service.

Vertical Pod Autoscaler (VPA) changes the CPU and memory requests and limits of the pods, essentially scaling them vertically rather than horizontally. This does not allow for rapid scaling since new instances of the pods are not created.

B. Use a Vertical Pod Autoscaler to scale the containers, and expose them via a NodePort Service.

Again, VPA is not suitable for rapid scaling. NodePort Service exposes the service on a static port on each node's IP, which is unnecessary if the service only needs to be accessed within the cluster.

D. Use a Horizontal Pod Autoscaler to scale the containers, and expose them via a NodePort Service.

While Horizontal Pod Autoscaler is the correct approach for rapid scaling, using a NodePort Service is unnecessary in this context since the service only needs to be accessed within the cluster. NodePort exposes the service outside the cluster, which doesn't match the requirement for intra-cluster access only.



Correct Answer:

C. Use a Horizontal Pod Autoscaler to scale the containers, and expose them via a ClusterIP Service.

For a service that needs to be accessed only by other services within the same cluster and must quickly scale in response to changing load, you should use a Horizontal Pod Autoscaler (HPA) to scale the number of pods in the deployment based on CPU or memory utilization (or custom metrics). This allows the service to add or remove replicas as needed, providing rapid scaling in response to demand.

A ClusterIP Service is the right type to use when you only need intra-cluster access. It provides a single IP address that internal clients can use to connect to any of the service's pods.

Links:

https://cloud.google.com/kubernetes-engine/docs/concepts/service#services_of_type_clusterip

https://cloud.google.com/kubernetes-engine/docs/concepts/horizontalpodautoscaler

#

### 8. Your application is running in multiple Google Kubernetes Engine clusters. It is managed by a Deployment in each cluster. The Deployment has created multiple replicas of your Pod in each cluster. You want to view the logs sent to stdout for all of the replicas in your Deployment in all clusters.

Which command should you use?

- A. kubectl logs [PARAM]

- B. gcloud logging read [PARAM]

- C. kubectl exec -it [PARAM] journalctl

- D. gcloud compute ssh [PARAM] --command='sudo journalctl'

### Ans: B


Incorrect Answers:

A. kubectl logs [PARAM]

Doesn't have the functionality to view logs from all replicas across all clusters.

C. kubectl exec -it [PARAM] journalctl

would be used to execute a command within a specific Pod, not to get logs from all replicas in a Deployment.

D. gcloud compute ssh [PARAM] --command='sudo journalctl'

would be used to SSH into a Compute Engine instance and run a command, not to get logs from a GKE Deployment.



Correct Answer:

B. gcloud logging read [PARAM]

https://cloud.google.com/blog/products/management-tools/using-logging-your-apps-running-kubernetes-engine: "gcloud command line tool – Using the gcloud logging read command, select the appropriate cluster, node, pod and container logs."



Links:

https://cloud.google.com/logging/docs/reference/tools/gcloud-logging#examples_2

https://cloud.google.com/blog/products/management-tools/using-logging-your-apps-running-kubernetes-engine

https://stackoverflow.com/questions/62007471/how-to-view-container-logs-via-stackdriver-on-gke


### 9. You need to configure a Deployment on Google Kubernetes Engine (GKE). You want to include a check that verifies that the containers can connect to the database. If the Pod is failing to connect, you want a script on the container to run to complete a graceful shutdown.

How should you configure the Deployment?

- A. Create two jobs: one that checks whether the container can connect to the database, and another that runs the shutdown script if the Pod is failing.

- B. Create the Deployment with a livenessProbe for the container that will fail if the container can't connect to the database. Configure a Prestop lifecycle handler that runs the shutdown script if the container is failing.

- C. Create the Deployment with a PostStart lifecycle handler that checks the service availability. Configure a PreStop lifecycle handler that runs the shutdown script if the container is failing.

- D. Create the Deployment with an initContainer that checks the service availability. Configure a Prestop lifecycle handler that runs the shutdown script if the Pod is failing.

### Ans: B

Incorrect Answers:

A. Create two jobs: one that checks whether the container can connect to the database, and another that runs the shutdown script if the Pod is failing.

Jobs are typically used for batch processing and are not suitable for continuous monitoring or handling graceful shutdowns of a running container.

C. Create the Deployment with a PostStart lifecycle handler that checks the service availability. Configure a PreStop lifecycle handler that runs the shutdown script if the container is failing.

PostStart handler would only be executed once, right after the container starts, and would not continuously monitor the connection to the database. Also, configuring a PreStop handler without a condition (e.g., liveness probe failure) doesn't align with the need to run the shutdown script only if the container is failing.

D. Create the Deployment with an initContainer that checks the service availability. Configure a Prestop lifecycle handler that runs the shutdown script if the Pod is failing.

InitContainers are used to set up conditions that must be met before the main container starts, so using an initContainer would not continuously monitor the database connection once the container is running. It also doesn't align with the requirement to run a script if the Pod is failing after it has been initialized.



Correct Answer:

B. Create the Deployment with a livenessProbe for the container that will fail if the container can't connect to the database. Configure a Prestop lifecycle handler that runs the shutdown script if the container is failing.

Create the Deployment with a livenessProbe for the container that will fail if the container can't connect to the database. Utilizing a liveness probe allows Kubernetes to check the connection to the database continuously. If the container fails to connect to the database, the liveness probe will fail, triggering Kubernetes to restart the container.

Configure a PreStop lifecycle handler that runs the shutdown script if the container is failing. According to Kubernetes documentation, the PreStop hook is called immediately before a container is terminated due to various reasons, such as an API request, liveness probe failure, or other management events. The PreStop hook is a good option for triggering a graceful shutdown without modifying the application, as mentioned in Google Cloud's best practices     This hook must complete before the TERM signal to stop the container can be sent. The Pod's termination grace period countdown begins before the PreStop hook is executed, so regardless of the outcome of the handler, the container will eventually terminate within the Pod's termination grace period.

By combining these two features, you can ensure that the containers are continuously monitored for connectivity to the database and that a graceful shutdown script is executed if the container is failing.



Links:

https://cloud.google.com/architecture/best-practices-for-running-cost-effective-kubernetes-applications-on-gke#make_sure_your_applications_are_shutting_down_in_accordance_with_kubernetes_expectations



https://kubernetes.io/docs/concepts/containers/container-lifecycle-hooks/#hook-details

### 10. You are porting an existing Apache/MySQL/PHP application stack from a single machine to Google

Kubernetes Engine. You need to determine how to containerize the application. Your approach should follow Google-recommended best practices for availability.

What should you do?

- A. Package each component in a separate container. Implement readiness and liveness probes.
- B. Package the application in a single container. Use a process management tool to manage each component.
- C. Package each component in a separate container. Use a script to orchestrate the launch of the components.
- D. Package the application in a single container. Use a bash script as an entrypoint to the container, and then spawn each component as a background job.

### Ans: A

Incorrect Answers:

B. Package the application in a single container. Use a process management tool to manage each component.

This approach violates the principle of one process per container, making the system harder to manage, scale, and troubleshoot. If one process fails, it can affect the entire container, leading to more downtime and complexity in isolating issues.

C. Package each component in a separate container. Use a script to orchestrate the launch of the components.

While separating each component into a different container aligns with best practices, the use of custom scripts for orchestration doesn't leverage Kubernetes' native capabilities for managing containers. This may lead to higher maintenance costs and less effective management compared to using Kubernetes' built-in orchestration features.

D. Package the application in a single container. Use a bash script as an entrypoint to the container, and then spawn each component as a background job.

Again, this option fails to follow the one process per container principle. Managing multiple background jobs within a single container can lead to tangled dependencies and make it difficult to diagnose issues. If one background job fails, it could affect the entire container. The use of bash scripts for management also doesn't take advantage of Kubernetes' orchestration features, leading to a more fragile and less scalable system.



Correct Answer:

A. Package each component in a separate container. Implement readiness and liveness probes.

By packaging each component in a separate container and implementing readiness and liveness probes, aligns with best practices for containerization and leverages Kubernetes' features to manage the containers efficiently and effectively.



Links:

https://cloud.google.com/architecture/best-practices-for-building-containers#package_a_single_app_per_container

### 11. You are a SaaS provider deploying dedicated blogging software to customers in your Google Kubernetes Engine (GKE) cluster. You want to configure a secure multi-tenant platform to ensure that each customer has access to only their own blog and can't affect the workloads of other customers.

What should you do?

- A. Enable Application-layer Secrets on the GKE cluster to protect the cluster.

- B. Deploy a namespace per tenant and use Network Policies in each blog deployment.

- C. Use GKE Audit Logging to identify malicious containers and delete them on discovery.

- D. Build a custom image of the blogging software and use Binary Authorization to prevent untrusted image deployments.

### Ans: C

ncorrect Answers:

A. Enable Application-layer Secrets on the GKE cluster to protect the cluster.

This does not address the multi-tenancy requirements, as it's more about protecting secrets rather than isolating tenants.

C. Use GKE Audit Logging to identify malicious containers and delete them on discovery.

While audit logging can help in identifying suspicious or unauthorized activities, it doesn't directly provide isolation or restrictions between tenants.

D. Build a custom image of the blogging software and use Binary Authorization to prevent untrusted image deployments.

Binary Authorization ensures that only trusted container images are deployed, but it doesn't provide isolation between different tenants or control over access to individual blogs.



Correct Answer:

B. Deploy a namespace per tenant and use Network Policies in each blog deployment.

By creating a separate namespace for each tenant, you can isolate resources at the Kubernetes level, ensuring that each tenant's workloads are separated from others.

Implementing Network Policies further restricts communication between different tenants, enforcing the isolation at the network level and ensuring that one tenant's workloads can't interact with another's.



Links:

https://cloud.google.com/kubernetes-engine/docs/concepts/multitenancy-overview#network_policies


### 12. One of your deployed applications in Google Kubernetes Engine (GKE) is having intermittent performance issues. Your team uses a third-party logging solution. You want to install this solution on each node in your GKE cluster so you can view the logs.

What should you do?

- A. Deploy the third-party solution as a DaemonSet

- B. Modify your container image to include the monitoring software

- C. Use SSH to connect to the GKE node, and install the software manually

- D. Deploy the third-party solution using Terraform and deploy the logging Pod as a Kubernetes Deployment

### Ans: A

ncorrect Answers:

B. Modify your container image to include the monitoring software

This would embed the logging solution within the application container itself. If the logging solution needs to be deployed to every node in the cluster, including nodes that may not be running this particular application, then this approach wouldn't work.

C. Use SSH to connect to the GKE node, and install the software manually

Manual installation does not follow best practices for maintaining infrastructure, particularly in Kubernetes. It introduces difficulties in maintaining consistency across nodes and recovering from node failures. It's also worth noting that GKE nodes are often managed and may not permit direct access for such changes.

D. Deploy the third-party solution using Terraform and deploy the logging Pod as a Kubernetes Deployment

Deploying the logging solution as a standard Deployment wouldn't ensure that an instance of the logging solution is running on every node. A Deployment is designed to ensure that a specified number of replicas of your application are running, not to enforce that the application runs on every node in your cluster.



Correct Answer:

A. Deploy the third-party solution as a DaemonSet

A DaemonSet ensures that all or some worker nodes run a copy of a Pod. As nodes are added to the cluster, Pods are added to them. If you want to deploy a monitoring or logging agent to every node in your cluster, then a DaemonSet is the correct way to do it.

Links:

https://kubernetes.io/docs/concepts/workloads/controllers/daemonset

https://cloud.google.com/kubernetes-engine/docs/concepts/daemonset#usage_patterns


### 13. You are a cluster administrator for Google Kubernetes Engine (GKE). Your organization's clusters are enrolled in a release channel. You need to stay informed about relevant events affecting your GKE clusters, such as available upgrades and security bulletins.

What should you do?

- A. Set up cluster notifications to be sent to a Pub/Sub topic.

- B. Perform a scheduled query against the google_cloud_release_notes BigQuery dataset.

- C. Query the GKE API to check for available versions.

- D. Create an RSS subscription to receive a daily summary of the GKE release notes.


### Ans: A

Incorrect Answers:

B. Perform a scheduled query against the google_cloud_release_notes BigQuery dataset.

This approach involves using BigQuery, Google's data warehouse service, to periodically query the google_cloud_release_notes dataset for updates relevant to GKE. While this can provide comprehensive information, including details about releases and updates, it requires setting up and maintaining scheduled queries. This method might not be as immediate or real-time as other notification systems and could require more effort to filter and parse the information specifically for GKE.

C. Query the GKE API to check for available versions.

By querying the GKE API for available versions, you can directly obtain information about the latest versions and updates for GKE. This method allows for a targeted approach to check specifically for version updates. However, it might not provide a comprehensive overview of all relevant events like security bulletins and requires regular API calls to stay updated.

D. Create an RSS subscription to receive a daily summary of the GKE release notes.

Subscribing to an RSS feed for GKE release notes is a straightforward way to receive daily summaries of updates and changes. This method ensures that you are regularly informed about new releases, upgrades, and potentially security bulletins. However, it might not provide the immediacy of other methods like Pub/Sub notifications and typically requires manual review of the updates.

Correct answer:

A. Set up cluster notifications to be sent to a Pub/Sub topic.

This option involves configuring Google Cloud Pub/Sub to receive notifications related to your GKE clusters. Pub/Sub is a messaging service that can be used to stream event data. By setting up cluster notifications in this way, you would be able to receive real-time updates on events like cluster upgrades or security issues. This method is highly efficient for automated monitoring and integrating with other systems or alerting mechanisms you might have in place.

Links:

https://cloud.google.com/kubernetes-engine/docs/concepts/cluster-notifications

https://cloud.google.com/kubernetes-engine/docs/concepts/release-channels#channels

### 14. You have containerized a legacy application that stores its configuration on an NFS share. You need to deploy this application to Google Kubernetes Engine (GKE) and do not want the application serving traffic until after the configuration has been retrieved.

What should you do?

- A. Use the gsutil utility to copy files from within the Docker container at startup, and start the service using an ENTRYPOINT script.

- B. Create a PersistentVolumeClaim on the GKE cluster. Access the configuration files from the volume, and start the service using an ENTRYPOINT script.

- C. Use the COPY statement in the Dockerfile to load the configuration into the container image. Verify that the configuration is available, and start the service using an ENTRYPOINT script.

- D. Add a startup script to the GKE instance group to mount the NFS share at node startup. Copy the configuration files into the container, and start the service using an ENTRYPOINT script.

### Ans: B

Incorrect Answers:

A. Use the gsutil utility to copy files from within the Docker container at startup, and start the service using an ENTRYPOINT script.

Is incorrect because gsutil is a command-line tool for interacting with Google Cloud Storage, not for managing containerized applications or NFS shares.

C. Use the COPY statement in the Dockerfile to load the configuration into the container image. Verify that the configuration is available, and start the service using an ENTRYPOINT script.

Is incorrect because storing configuration data in a Docker image isn't a best practice for Kubernetes. It reduces the portability of the container and doesn't fit the cloud-native model of keeping configuration and secrets outside of the application.

D. Add a startup script to the GKE instance group to mount the NFS share at node startup. Copy the configuration files into the container, and start the service using an ENTRYPOINT script.

Is incorrect because GKE manages the underlying node infrastructure, including startup scripts. Also, GKE abstracts away individual node access to the point where directly scripting individual node behavior is not practical or even possible.



Correct Answer:

B. Create a PersistentVolumeClaim on the GKE cluster. Access the configuration files from the volume, and start the service using an ENTRYPOINT script.

This option leverages Kubernetes' native capabilities for managing storage resources, which includes support for NFS. The application can then access its configuration from the NFS share as if it were local to the container. The container will not serve traffic until the ENTRYPOINT script starts the service, which should only happen after the configuration has been successfully retrieved.

Links:

https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes

https://cloud.google.com/filestore/docs/accessing-fileshares

https://cloud.google.com/storage/docs/gcs-fuse

### 15. You are developing a JPEG image-resizing API hosted on Google Kubernetes Engine (GKE). Callers of the service will exist within the same GKE cluster. You want clients to be able to get the IP address of the service.

What should you do?


- A. Define a GKE Service. Clients should use the name of the A record in Cloud DNS to find the service's cluster IP address.

- B. Define a GKE Service. Clients should use the service name in the URL to connect to the service.

- C. Define a GKE Endpoint. Clients should obtain the endpoint name from the appropriate environment variable in the client container.

- D. Define a GKE Endpoint. Clients should get the endpoint name from Cloud DNS.

### Ans: B

Incorrect Answers:

A. Define a GKE Service. Clients should use the name of the A record in Cloud DNS to find the service's cluster IP address.

While defining a GKE Service is correct, typically within a Kubernetes cluster, you do not need to rely on an A record in Cloud DNS. Pods within the cluster can directly use the service name.

C. Define a GKE Endpoint. Clients should obtain the endpoint name from the appropriate environment variable in the client container.

D. Define a GKE Endpoint. Clients should get the endpoint name from Cloud DNS.

Kubernetes doesn't have a concept called a "GKE Endpoint." Endpoints in Kubernetes are a part of services and are used internally to track the IPs of pods that the service should proxy to. These are not something that clients interact with directly.

Correct Answer:

B. Define a GKE Service. Clients should use the service name in the URL to connect to the service.

This is the correct way to allow internal communication within the cluster. The service name acts as a DNS name, and the service's cluster IP is automatically resolved within the cluster.

Links:

https://cloud.google.com/kubernetes-engine/docs/concepts/service-discovery