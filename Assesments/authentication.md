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

