### 1. You recently deployed your application in Google Kubernetes Engine, and now need to release a new version of your application. You need the ability to instantly roll back to the previous version in case there are issues with the new version.

Which deployment model should you use?

- A. Perform a rolling deployment, and test your new application after the deployment is complete.

- B. Perform A/B testing, and test your application periodically after the new tests are implemented.

- C. Perform a blue/green deployment, and test your new application after the deployment is. complete.

- D. Perform a canary deployment, and test your new application periodically after the new version is deployed.

### Ans: C

Incorrect Answers:

A. Perform a rolling deployment, and test your new application after the deployment is complete.

Rolling deployments gradually replace instances of the old version with the new version. While this allows for zero downtime, an instant rollback might be more complex, as the system has to reverse the gradual changes.

B. Perform A/B testing, and test your application periodically after the new tests are implemented.

A/B testing involves splitting users into different groups to test different versions of an application. It's more about comparing performance or usability rather than providing a mechanism for instant rollback.

D. Perform a canary deployment, and test your new application periodically after the new version is deployed.

Canary deployments release the new version to a small subset of users before a full rollout. While it helps in detecting issues early, it might not provide the mechanism for an instant rollback to the previous version for all users.



Correct Answer:

C. Perform a blue/green deployment, and test your new application after the deployment is. complete.

Blue/green deployments involve having two separate environments: one running the old version (blue) and the other running the new version (green). By simply redirecting the traffic, you can switch between these versions. If there are any problems with the green environment, you can instantly revert to the blue environment. Thus, the blue/green deployment model best suits the requirement to instantly roll back to the previous version if there are issues with the new version.

Links:

https://cloud.google.com/architecture/application-deployment-and-testing-strategies#choosing_the_right_strategy