### 1. You need to build a public API that authenticates, enforces quotas, and reports metrics for API callers.
Which tool should you use to complete this architecture?

- A. App Engine
- B. Cloud Endpoints
- C. Identity-Aware Proxy
- D. GKE Ingress for HTTP(S) Load Balancing

### Ans: B

A. App Engine

Cloud Run provides none of these features.

C. Identity-Aware Proxy

IAP provides only authentication.

D. GKE Ingress for HTTP(S) Load Balancing

GKE Ingress provides none of these features.



Correct Answer:

B. Cloud Endpoints

All three features, authentication, quotas/rate limiting and metrics are the core features of Cloud Endpoints.

Links:

https://cloud.google.com/endpoints/docs/openapi/quotas-configure

https://cloud.google.com/endpoints/docs/openapi/monitoring-your-api


### 2. You are developing a corporate tool on Compute Engine for the finance department, which needs to authenticate users and verify that they are in the finance department. All company employees use G Suite.

What should you do?

- A. Enable Cloud Identity-Aware Proxy on the HTTP(s) load balancer and restrict access to a Google Group containing users in the finance department. Verify the provided JSON Web Token within the application.

- B. Enable Cloud Identity-Aware Proxy on the HTTP(s) load balancer and restrict access to a Google Group containing users in the finance department. Issue client-side certificates to everybody in the finance team and verify the certificates in the application.

- C. Configure Cloud Armor Security Policies to restrict access to only corporate IP address ranges. Verify the provided JSON Web Token within the application.

- D. Configure Cloud Armor Security Policies to restrict access to only corporate IP address ranges. Issue client side certificates to everybody in the finance team and verify the certificates in the application.

### Ans: A

Incorrect Answers:

B. Enable Cloud Identity-Aware Proxy on the HTTP(s) load balancer and restrict access to a Google Group containing users in the finance department. Issue client-side certificates to everybody in the finance team and verify the certificates in the application.

Adds unnecessary complexity by issuing client-side certificates without any clear requirement or benefit for this case.

C. Configure Cloud Armor Security Policies to restrict access to only corporate IP address ranges. Verify the provided JSON Web Token within the application.

D. Configure Cloud Armor Security Policies to restrict access to only corporate IP address ranges. Issue client side certificates to everybody in the finance team and verify the certificates in the application.

Options C and D rely on Cloud Armor Security Policies to restrict access based on IP addresses, which is not suitable for authenticating individual users and verifying their departmental affiliation. It doesn't utilize the fact that all company employees are using G Suite, and IP-based restrictions might not be sufficient to limit access to the finance department only.



Correct Answer:

A. Enable Cloud Identity-Aware Proxy on the HTTP(s) load balancer and restrict access to a Google Group containing users in the finance department. Verify the provided JSON Web Token within the application.

Enable Cloud Identity-Aware Proxy (IAP) on the HTTP(s) load balancer: IAP controls access to your cloud applications running on Google Cloud. By verifying identity and context to determine if a user should be allowed to access the application, it can ensure that only the right people have access.

Restrict access to a Google Group containing users in the finance department: This ensures that only members of the finance department's specific group have access. IAP can be configured to grant access based on Google Workspace groups.

Verify the provided JSON Web Token within the application: IAP sets a JSON Web Token (JWT), which the application can validate to ensure that the request was authorized by IAP.

Links:

https://cloud.google.com/iap/docs/signed-headers-howto#securing_iap_headers


### 3. You are developing an internal application that will allow employees to organize community events within your company. You deployed your application on a single Compute Engine instance. Your company uses Google Workspace (formerly G Suite), and you need to ensure that the company employees can authenticate to the application from anywhere.

What should you do?

- A. Add a public IP address to your instance, and restrict access to the instance using firewall rules. Allow your company's proxy as the only source IP address.

- B. Add an HTTP(S) load balancer in front of the instance, and set up Identity-Aware Proxy (IAP). Configure the IAP settings to allow your company domain to access the website.

- C. Set up a VPN tunnel between your company network and your instance's VPC location on Google Cloud. Configure the required firewall rules and routing information to both the on-premises and Google Cloud networks.

- D. Add a public IP address to your instance, and allow traffic from the internet. Generate a random hash, and create a subdomain that includes this hash and points to your instance. Distribute this DNS address to your company's employees.

### Ans: B

Incorrect Answers:

A. Add a public IP address to your instance, and restrict access to the instance using firewall rules. Allow your company's proxy as the only source IP address.

This method lacks authentication based on company domain and could cause issues if employees are trying to access the application from outside the company network.

C. Set up a VPN tunnel between your company network and your instance's VPC location on Google Cloud. Configure the required firewall rules and routing information to both the on-premises and Google Cloud networks.

This method would make the application accessible only from within the company's network or through a VPN connection, thus potentially preventing employees from accessing the application from other locations.

D. Add a public IP address to your instance, and allow traffic from the internet. Generate a random hash, and create a subdomain that includes this hash and points to your instance. Distribute this DNS address to your company's employees.

This method doesn't provide any authentication based on the user's identity. It relies on a shared secret (the hash in the subdomain), which does not verify that a user is an employee.



Correct Answer:

B. Add an HTTP(S) load balancer in front of the instance, and set up Identity-Aware Proxy (IAP). Configure the IAP settings to allow your company domain to access the website.

Identity-Aware Proxy (IAP): It helps control access to applications running on Google Cloud, allowing you to set access levels based on the identity and group membership of users (such as your company domain).

HTTP(S) Load Balancer: It allows you to route incoming HTTP(S) traffic to different instances based on various parameters, adding scalability and control.

Therefore, option B is the best approach, as it allows access based on the user's identity and ensures that only employees from the company domain can authenticate to the application.



Links:

https://cloud.google.com/iap/docs/concepts-overview#how_iap_works

https://cloud.google.com/blog/topics/developers-practitioners/control-access-your-web-sites-identity-aware-proxy

### 4. You are creating a web application that runs in a Compute Engine instance and writes a file to any user's Google Drive. You need to configure the application to authenticate to the Google Drive API.

What should you do?

- A. Use an OAuth Client ID that uses the https://www.googleapis.com/auth/drive.file scope to obtain an access token for each user.

- B. Use an OAuth Client ID with delegated domain-wide authority.

- C. Use the App Engine service account and https://www.googleapis.com/auth/drive.file scope to generate a signed JSON Web Token (JWT).

- D. Use the App Engine service account with delegated domain-wide authority.

### Ans: A

Incorrect Answers:

B. Use an OAuth Client ID with delegated domain-wide authority.

Domain-wide authority is typically used for G Suite domain administrators to grant third-party applications access to the data of all users in the domain. It's not needed for this scenario.

C. Use the App Engine service account and https://www.googleapis.com/auth/drive.file scope to generate a signed JSON Web Token (JWT).

D. Use the App Engine service account with delegated domain-wide authority.

Option C is incorrect because a Compute Engine instance is being used, not App Engine. Moreover, a service account represents an application, not a user, so using a service account wouldn't allow the app to write files to a user's Google Drive.

Option D is also incorrect for the same reasons. In addition, domain-wide authority is unnecessary in this scenario and does not fit the requirements.



Correct Answer:

A. Use an OAuth Client ID that uses the https://www.googleapis.com/auth/drive.file scope to obtain an access token for each user.

Your web application needs to authenticate on behalf of each user to the Google Drive API in order to write a file to their Drive. This is typically done using OAuth 2.0, which allows users to grant your application permissions to perform actions on their behalf without sharing their password.

The https://www.googleapis.com/auth/drive.file scope allows the application to view and manage Google Drive files that were created by the app.

Links:

https://developers.google.com/drive/api/guides/api-specific-auth

https://developers.google.com/drive/api/guides/about-auth

### 5. You are developing a microservice-based application that will run on Google Kubernetes Engine (GKE). Some of the services need to access different Google Cloud APIs. How should you set up authentication for these services in the cluster, following Google-recommended best practices? (Choose two options.)

- A. Use the service account attached to the GKE node.

- B. Enable Workload Identity in the cluster using the gcloud command-line tool.

- C. Access Google service account keys from a secret management service.

- D. Store Google service account keys in a central secret management service.

- E. Use gcloud to bind the Kubernetes service account to the Google service account using roles/iam.workloadIdentity.

### Ans: B & E

Incorrect Answers:

A. Use the service account attached to the GKE node.

Using the node's service account can lead to over-provisioned permissions and lack of granular control. It's better to use Workload Identity to bind specific Google service accounts to the services that need them.

C. Access Google service account keys from a secret management service.

Managing keys manually, even with a secret management service, can be error-prone and less secure compared to using Workload Identity.

D. Store Google service account keys in a central secret management service.

Similar to option C, this method involves manual management of keys, which can lead to complexity and potential security risks.


Correct Answer:

B. Enable Workload Identity in the cluster using the gcloud command-line tool.

Workload Identity is the recommended way to manage authentication for applications running on GKE. It allows you to bind Kubernetes service accounts to Google service accounts, enabling the application to authenticate to Google Cloud services without needing to manage keys manually.

E. Use gcloud to bind the Kubernetes service account to the Google service account using roles/iam.workloadIdentity.

This step is part of setting up Workload Identity. By binding the Kubernetes service account to a Google service account, you enable the application to assume the identity and permissions of the Google service account. This makes it easy to control and audit access to Google Cloud services.

Links:

https://cloud.google.com/kubernetes-engine/docs/tutorials/authenticating-to-cloud-platform#use_workload_identity

https://cloud.google.com/kubernetes-engine/docs/how-to/kubernetes-service-accounts