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







