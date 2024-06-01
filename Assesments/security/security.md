### 1. You are running a web application on Google Kubernetes Engine that you inherited. You want to determine whether the application is using libraries with known vulnerabilities or is vulnerable to XSS attacks.

Which service should you use?

- A. Google Cloud Armor
- B. Debugger
- C. Web Security Scanner
- D. Error Reporting

### Ans: C
The correct service, Web Security Scanner (Option C), is designed to perform precisely this kind of vulnerability detection by scanning, identifying, and reporting issues related to common web application vulnerabilities, including XSS.

https://cloud.google.com/security-command-center/docs/concepts-web-security-scanner-overview

### 2. Your team is responsible for maintaining an application that aggregates news articles from many different sources. Your monitoring dashboard contains publicly accessible real-time reports and runs on a Compute Engine instance as a web application. External stakeholders and analysts need to access these reports via a secure channel without authentication.

How should you configure this secure channel?

- A. Add a public IP address to the instance. Use the service account key of the instance to encrypt the traffic.

- B. Use Cloud Scheduler to trigger Cloud Build every hour to create an export from the reports. Store the reports in a public Cloud Storage bucket.

- C. Add an HTTP(S) load balancer in front of the monitoring dashboard. Configure Identity-Aware Proxy to secure the communication channel.

- D. Add an HTTP(S) load balancer in front of the monitoring dashboard. Set up a Google-managed SSL certificate on the load balancer for traffic encryption.

### Ans: D

A. Add a public IP address to the instance. Use the service account key of the instance to encrypt the traffic.

Encrypting the traffic using the service account key of the instance would not be an appropriate or standard way to secure HTTP communication. SSL/TLS is the common method to secure such connections.

B. Use Cloud Scheduler to trigger Cloud Build every hour to create an export from the reports. Store the reports in a public Cloud Storage bucket.

Storing the reports in a public Cloud Storage bucket would provide access to the reports, but it doesn't meet the requirement for real-time access. This method would introduce a delay, as the reports would be generated and stored every hour, rather than providing immediate, real-time access.

C. Add an HTTP(S) load balancer in front of the monitoring dashboard. Configure Identity-Aware Proxy to secure the communication channel.

Identity-Aware Proxy (IAP) is used to control access to applications running in Google Cloud, typically by requiring user authentication and authorization. Since the requirement is to provide access without authentication, this option does not fit the scenario.

D. Add an HTTP(S) load balancer in front of the monitoring dashboard. Set up a Google-managed SSL certificate on the load balancer for traffic encryption.

The question emphasizes the need for secure channel access to publicly accessible real-time reports without authentication. Therefore, an SSL certificate would provide the necessary encryption for secure communication.

By placing an HTTP(S) load balancer in front of the monitoring dashboard and using a Google-managed SSL certificate, the traffic between users and the application would be encrypted, thus ensuring secure access.

https://cloud.google.com/load-balancing/docs/ssl-certificates/google-managed-certs

### 3. You manage a microservices application on Google Kubernetes Engine (GKE) using Istio. You secure the communication channels between your microservices by implementing an Istio AuthorizationPolicy, a Kubernetes NetworkPolicy, and mTLS on your GKE cluster. You discover that HTTP requests between two Pods to specific URLs fail, while other requests to other URLs succeed.

What is the cause of the connection issue?

- A. A Kubernetes NetworkPolicy resource is blocking HTTP traffic between the Pods.
- B. The Pod initiating the HTTP requests is attempting to connect to the target Pod via an incorrect TCP port.
- C. The Authorization Policy of your cluster is blocking HTTP requests for specific paths within your application.
- D. The cluster has mTLS configured in permissive mode, but the Pod's sidecar proxy is sending unencrypted traffic in plain text.

### Ans: C

A. A Kubernetes NetworkPolicy resource is blocking HTTP traffic between the Pods.

A Kubernetes NetworkPolicy would block all traffic between the Pods, not just specific URLs. This doesn't align with the problem described.

B. The Pod initiating the HTTP requests is attempting to connect to the target Pod via an incorrect TCP port.

An incorrect TCP port would also result in all traffic between the Pods failing, not just specific URLs.

D. The cluster has mTLS configured in permissive mode, but the Pod's sidecar proxy is sending unencrypted traffic in plain text.

mTLS configured in permissive mode would allow both encrypted and unencrypted traffic, so it would not explain the failure of specific URLs while other URLs succeed.



Correct Answer:

C. The Authorization Policy of your cluster is blocking HTTP requests for specific paths within your application.

Option C, stating that the Authorization Policy of the cluster is blocking HTTP requests for specific paths within the application, is the most likely cause for this issue. Istio's AuthorizationPolicy enables access control on who can do what to specific services or paths in your application.

Links:

https://istio.io/latest/docs/tasks/security/authorization/authz-http/

https://kubernetes.io/docs/concepts/services-networking/network-policies/

https://istio.io/latest/docs/tasks/security/authentication/mtls-migration/


### 4. Your company has a new security initiative that requires all data stored in Google Cloud to be encrypted by customer-managed encryption keys. You plan to use Cloud Key Management Service (KMS) to configure access to the keys. You need to follow the "separation of duties" principle and Google-recommended best practices.

What should you do? (Choose two options)

- A. Provision Cloud KMS in its own project.

- B. Do not assign an owner to the Cloud KMS project.

- C. Provision Cloud KMS in the project where the keys are being used.

- D. Grant the roles/cloudkms.admin role to the owner of the project where the keys from Cloud KMS are being used.

- E. Grant an owner role for the Cloud KMS project to a different user than the owner of the project where the keys from Cloud KMS are being used.

### Ans: A & B

Incorrect Answers:

C. Provision Cloud KMS in the project where the keys are being used.

Is not correct because co-locating Cloud KMS in the same project where keys are used could lead to mismanagement or unintended key access. It is best to keep these concerns separated.

D. Grant the roles/cloudkms.admin role to the owner of the project where the keys from Cloud KMS are being used.

Granting the cloudkms.admin role to the owner of the project where the keys are used violates the separation of duties principle. This would give one user the ability to both manage and use the keys, which could lead to unauthorized access or changes.

E. Grant an owner role for the Cloud KMS project to a different user than the owner of the project where the keys from Cloud KMS are being used.

(not recommended) If you must continue to use the owner role, ensure that it is granted to a different principal in your-key-project than the principal who is the owner of your-project. The owner can still use keys, but only in a single project.  (https://cloud.google.com/kms/docs/separation-of-duties#using_separate_project)



Correct Answer:

A. Provision Cloud KMS in its own project.

Creating Cloud Key Management Service (KMS) in its own project provides a clear boundary of responsibility and reduces the risk of accidental key deletion or modification.

B. Do not assign an owner to the Cloud KMS project.

(Recommended) Create your project key without an owner at the project level, and designate an Organization Admin granted at the organization level. Unlike an owner, an Organization Admin can't manage or use keys directly. They are restricted to setting IAM policies, which restrict who can manage and use keys. Using an organization-level node, you can further restrict permissions for projects within your organization. (https://cloud.google.com/kms/docs/separation-of-duties#using_separate_project)

Links:

https://cloud.google.com/kms/docs/separation-of-duties#using_separate_project
