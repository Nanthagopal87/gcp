### 1. You work for an organization that manages an ecommerce site. Your application is deployed behind a global HTTP(S) load balancer. You need to test a new product recommendation algorithm. You plan to use A/B testing to determine the new algorithm’s effect on sales in a randomized way.

How should you test this feature?

- A. Split traffic between versions using weights.

- B. Enable the new recommendation feature flag on a single instance.

- C. Mirror traffic to the new version of your application.

- D. Use HTTP header-based routing.

### Ans: A

B. Enable the new recommendation feature flag on a single instance.

Enabling the new recommendation feature on a single instance wouldn't provide a controlled experiment where you can compare the two versions properly.

C. Mirror traffic to the new version of your application.

Mirroring traffic to the new version would send the same requests to both versions but would typically only use the responses from the old version. This approach is more suitable for assessing performance and doesn't help in an A/B test where you want to measure user interaction and conversion.

D. Use HTTP header-based routing.

HTTP header-based routing is used to direct traffic based on specific header values, such as user-agent or custom headers. It could be used for A/B testing, but the question doesn't provide information that would indicate this approach is needed. Randomly splitting traffic using weights provides a more straightforward way to accomplish the A/B testing goal.



Correct Answer:

A. Split traffic between versions using weights.

By splitting traffic between two versions (the current algorithm and the new algorithm) using weights, you can control the percentage of users who see each version. This allows you to perform a randomized experiment where part of the users experiences the current version, and part experiences the new version. You can then compare the effects on sales.

Links:

https://cloud.google.com/traffic-director/docs/advanced-traffic-management#weight-based_traffic_splitting_for_safer_deployments


### 2. You have deployed an HTTP(s) Load Balancer with the gcloud commands shown below.

Health checks to port 80 on the Compute Engine virtual machine instance are failing and no traffic is sent to your instances. The objective is to resolve the issue.

Which commands should you run?

- A. gcloud compute instances add-access-config ${NAME}-backend-instance-1

- B. gcloud compute instances add-tags ${NAME}-backend-instance-1 --tags http-server

- C. gcloud compute firewall-rules create allow-lb --network load-balancer --allow tcp --source-ranges 130.211.0.0/22,35.191.0.0/16 --direction INGRESS

- D. gcloud compute firewall-rules create allow-lb --network load-balancer --allow tcp --destination-ranges 130.211.0.0/22,35.191.0.0/16 --direction EGRESS


Incorrect Answers:

A. gcloud compute instances add-access-config ${NAME}-backend-instance-1

Option A will not help because it is used to add an external IP address to an instance, which is not necessary for the Load Balancer work.

B. gcloud compute instances add-tags ${NAME}-backend-instance-1 --tags http-server

B is related to adding tags to an instance, but without corresponding firewall rules, it won't solve the problem. This command used to apply metadata to an instance, which is not related to the Load Balancer.

D. gcloud compute firewall-rules create allow-lb --network load-balancer --allow tcp --destination-ranges 130.211.0.0/22,35.191.0.0/16 --direction EGRESS

D is creating a firewall rule for outgoing (EGRESS) traffic, but the issue here is with incoming (INGRESS) health checks.



Correct Answer:

C. gcloud compute firewall-rules create allow-lb --network load-balancer --allow tcp --source-ranges 130.211.0.0/22,35.191.0.0/16 --direction INGRESS

This command creates a firewall rule that allows incoming TCP traffic on port 80 from the specified source ranges, which are the IP address ranges used by Google's load balancers for health checking.

Please note, the correct command should specify the TCP port 80, as shown in the corrected option above.

Link: https://cloud.google.com/vpc/docs/special-configurations

