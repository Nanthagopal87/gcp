### 1. You have an application deployed in production. When a new version is deployed, some issues don't arise until the application receives traffic from users in production. You want to reduce both the impact and the number of users affected.

Which deployment strategy should you use?

- A. Blue/green deployment

- B. Canary deployment

- C. Rolling deployment

- D. Recreate deployment

### Ans: B

Incorrect Answers:

A. Blue/green deployment

This approach allows you to switch between two separate environments (blue for the running version and green for the new version). It doesn't specifically allow for testing with a subset of users to detect issues before rolling out to everyone.

C. Rolling deployment

Rolling deployment updates instances incrementally, one after the other. While it does allow for gradual rollout, it doesn't target a specific subset of users like Canary deployment does, so it's not as suitable for detecting user-specific issues.

D. Recreate deployment

This method involves taking down the old version and deploying the new version. All instances are replaced simultaneously, so it does not fit the requirement to reduce impact and test with a subset of users.



Correct Answer:

B. Canary deployment

Canary deployment gradually releases the new version to a small subset of users before making it available to everyone. This allows you to test how the new version behaves with real users in the production environment but with a limited audience, reducing both impact and number of users affected by potential issues. This is the right fit for the described situation.



Links:

https://cloud.google.com/architecture/application-deployment-and-testing-strategies#canary_test_pattern