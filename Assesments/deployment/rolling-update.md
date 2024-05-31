### 1. The new version of your containerized application has been tested and is ready to deploy to production on Google Kubernetes Engine.
You were not able to fully load-test the new version in pre-production environments, and you need to make sure that it does not have performance problems once deployed. Your deployment must be automated.
What should you do?

- A. Use Cloud Load Balancing to slowly ramp up traffic between versions. Use Cloud Monitoring to look for performance issues.

- B. Deploy the application via a continuous delivery pipeline using canary deployments. Use Cloud Monitoring to look for performance issues. and ramp up traffic as the metrics support it.

- C. Deploy the application via a continuous delivery pipeline using blue/green deployments. Use Cloud Monitoring to look for performance issues, and launch fully when the metrics support it.

- D. Deploy the application using kubectl and set the spec.updateStrategv.type to RollingUpdate. Use Cloud Monitoring to look for performance issues, and run the kubectl rollback command if there are any issues.

### Ans: D

Incorrect Answers:

A. Use Cloud Load Balancing to slowly ramp up traffic between versions. Use Cloud Monitoring to look for performance issues.

Cloud Load Balancing isn't a suitable tool for controlled rollouts of a new application version in a Kubernetes environment.

B. Deploy the application via a continuous delivery pipeline using canary deployments. Use Cloud Monitoring to look for performance issues. and ramp up traffic as the metrics support it.

Canary deployments are a good way to test a new version with a small subset of users, but this option does not match the selected correct answer.

C. Deploy the application via a continuous delivery pipeline using blue/green deployments. Use Cloud Monitoring to look for performance issues, and launch fully when the metrics support it.

Blue/green deployments enable quick switches between versions but are not tailored for gradually increasing exposure to a new version.



Correct Answer:

D. Deploy the application using kubectl and set the spec.updateStrategv.type to RollingUpdate. Use Cloud Monitoring to look for performance issues, and run the kubectl rollback command if there are any issues.

A RollingUpdate in Kubernetes allows for a gradual update of the application. If performance problems are detected through Cloud Monitoring, the deployment can be rolled back using kubectl rollback. This provides both the gradual exposure needed to detect issues and the automation to efficiently manage the deployment.



Links:

https://kubernetes.io/docs/tutorials/kubernetes-basics/update/update-intro/

https://cloud.google.com/kubernetes-engine/docs/how-to/updating-apps#overview