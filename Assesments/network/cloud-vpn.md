### 1. You recently migrated an on-premises monolithic application to a microservices application on Google Kubernetes Engine (GKE). The application has dependencies on backend services on-premises, including a CRM system and a MySQL database that contains personally identifiable information (PII). The backend services must remain on-premises to meet regulatory requirements.

You established a Cloud VPN connection between your on-premises data center and Google Cloud. You notice that some requests from your microservices application on GKE to the backend services are failing due to latency issues caused by fluctuating bandwidth, which is causing the application to crash.

How should you address the latency issues?

- A. Use Memorystore to cache frequently accessed PII data from the on-premises MySQL database

- B. Use Istio to create a service mesh that includes the microservices on GKE and the on-premises services

- C. Increase the number of Cloud VPN tunnels for the connection between Google Cloud and the on-premises services

- D. Decrease the network layer packet size by decreasing the Maximum Transmission Unit (MTU) value from its default value on Cloud VPN



### Ans: C

Incorrect Answers:

A. Use Memorystore to cache frequently accessed PII data from the on-premises MySQL database

While caching can reduce latency for some data access, it may not be applicable for PII data due to regulatory requirements. Plus, this doesn't address the fundamental issue of fluctuating bandwidth causing the problem.

B. Use Istio to create a service mesh that includes the microservices on GKE and the on-premises services

Service meshes like Istio can provide better control, observability, and routing. However, they do not inherently solve the problem of fluctuating bandwidth, so the latency issues would likely persist.

D. Decrease the network layer packet size by decreasing the Maximum Transmission Unit (MTU) value from its default value on Cloud VPN

Decreasing the MTU can lead to more packets being sent, but it won't necessarily solve the problem of fluctuating bandwidth and may even lead to more overhead, thus potentially worsening the problem.



Correct Answer:

C. Increase the number of Cloud VPN tunnels for the connection between Google Cloud and the on-premises services

Increasing the number of VPN tunnels can provide more bandwidth, which could help alleviate the latency issues. This approach directly addresses the root cause of the problem.

Links:

https://cloud.google.com/network-connectivity/docs/vpn/concepts/topologies#more-bandwidth

