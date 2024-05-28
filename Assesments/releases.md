### 1. You are designing a deployment technique for your new applications on Google Cloud. As part of your deployment planning, you want to use live traffic to gather performance metrics for both new and existing applications. You need to test against the full production load prior to launch.

What should you do?

- A. Use canary deployment

- B. Use blue/green deployment

- C. Use rolling updates deployment

- D. Use A/B testing with traffic mirroring during deployment

### Ans: D

A. Use canary deployment

Although useful for testing a new version with a subset of users, it doesn't offer the ability to test against the full production load prior to launch, as described in the scenario.

B. Use blue/green deployment

This approach doesn't enable simultaneous testing of both versions under the full production load; it's more about switching between two versions.

C. Use rolling updates deployment

This involves a gradual replacement and doesn't allow for a side-by-side comparison under full production load.

D. Use A/B testing with traffic mirroring during deployment

Option D's combination of A/B testing with traffic mirroring provides the desired capability to test both new and existing applications against the full production load, making it the correct choice for this scenario.

https://cloud.google.com/architecture/application-deployment-and-testing-strategies

### 2. Before promoting your new application code to production, you want to conduct testing across a variety of different users. Although this plan is risky, you want to test the new version of the application with production users and you want to control which users are forwarded to the new version of the application based on their operating system. If bugs are discovered in the new version, you want to roll back the newly deployed version of the application as quickly as possible.

What should you do?

- A. Deploy your application on Cloud Run. Use traffic splitting to direct a subset of user traffic to the new version based on the revision tag.

- B. Deploy your application on Google Kubernetes Engine with Anthos Service Mesh. Use traffic splitting to direct a subset of user traffic to the new version based on the user-agent header.

- C. Deploy your application on App Engine. Use traffic splitting to direct a subset of user traffic to the new version based on the IP address.

- D. Deploy your application on Compute Engine. Use Traffic Director to direct a subset of user traffic to the new version based on predefined weights.

### Ans: B

A. Deploy your application on Cloud Run. Use traffic splitting to direct a subset of user traffic to the new version based on the revision tag.

Option A (Cloud Run) allows for traffic splitting based on revision tags, but it doesn't provide control over user traffic based on the operating system (user-agent header).

C. Deploy your application on App Engine. Use traffic splitting to direct a subset of user traffic to the new version based on the IP address.

Option C (App Engine) allows for traffic splitting, but splitting based on IP address doesn't align with the need to route users based on their operating system.

D. Deploy your application on Compute Engine. Use Traffic Director to direct a subset of user traffic to the new version based on predefined weights.

Option D (Compute Engine with Traffic Director) enables traffic control based on predefined weights but doesn't provide the granularity required to route users based on their operating system.



Correct Answer:

B. Deploy your application on Google Kubernetes Engine with Anthos Service Mesh. Use traffic splitting to direct a subset of user traffic to the new version based on the user-agent header.

Option B allows for sophisticated routing and traffic control, including splitting traffic based on HTTP headers such as the user-agent. This makes it possible to route users to different versions of the application based on their operating system, meeting the requirement stated.

Links:

https://cloud.google.com/traffic-director/docs/ingress-traffic#sending-traffic

### 3. You are responsible for deploying a new API. That API will have three different URL paths:

https://yourcompany.com/students

https://yourcompany.com/teachers

https://yourcompany.com/classes

You need to configure each API URL path to invoke a different function in your code. What should you do?

- A. Create one Cloud Function as a backend service exposed using an HTTPS load balancer.

- B. Create three Cloud Functions exposed directly.

- C. Create one Cloud Function exposed directly.

- D. Create three Cloud Functions as three backend services exposed using an HTTPS load balancer.

### Ans: D

A. Create one Cloud Function as a backend service exposed using an HTTPS load balancer.

Creating one Cloud Function with a load balancer would not allow for different code paths based on the URL unless you add extra logic within the Cloud Function itself to handle routing, which can lead to unnecessary complexity.

B. Create three Cloud Functions exposed directly.

Creating three Cloud Functions exposed directly would mean that each one would have a separate URL, so you wouldn't be able to maintain the desired URL structure under "https://yourcompany.com".

C. Create one Cloud Function exposed directly.

Creating one Cloud Function exposed directly would not allow for different code paths based on the URL without internal routing logic, similar to option A.



Correct Answer:

D. Create three Cloud Functions as three backend services exposed using an HTTPS load balancer.

Since you have three distinct URL paths that need to invoke different functions in your code, you'll want to map each path to a separate backend service (in this case, Cloud Functions). By creating three separate Cloud Functions, you can design each one to handle the logic for a specific URL path.

Option D also includes the use of an HTTPS load balancer, which can be configured to route traffic to the correct backend service (Cloud Function) based on the URL path. This allows you to maintain a single domain while routing traffic to different Cloud Functions based on the path.

Links:

https://cloud.google.com/load-balancing/docs/https/setup-global-ext-https-serverless