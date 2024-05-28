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