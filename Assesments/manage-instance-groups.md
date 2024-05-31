### 1. Your application is deployed on hundreds of Compute Engine instances in a managed instance group (MIG) in multiple zones. You need to deploy a new instance template to fix a critical vulnerability immediately but must avoid impact to your service.

What setting should be made to the MIG after updating the instance template?

- A. Set the Max Surge to 100%.

- B. Set the Update mode to Opportunistic.

- C. Set the Maximum Unavailable to 100%.

- D. Set the Minimum Wait time to 0 seconds.

### Ans: D

Incorrect Answers:

A. Set the Max Surge to 100%.

Max Surge defines the number of additional instances that can be created during the update. Setting it to 100% would double the number of instances temporarily. While it can speed up the update process, it might also have other consequences, such as increased costs, and doesn't control the time between updates of individual instances.

B. Set the Update mode to Opportunistic.

As mentioned earlier, this mode updates instances only when they are recreated due to other activities. It doesn't provide a way to immediately update them to fix a critical vulnerability, making it unsuitable for the urgent update needed in this scenario.

C. Set the Maximum Unavailable to 100%.

This setting would allow all instances in the group to be unavailable simultaneously during the update, which is directly against the requirement to avoid impact to the service. This option would lead to downtime, making it incorrect for this situation.



Correct Answer:

D. Set the Minimum Wait time to 0 seconds.

This setting allows the update process to be as quick as possible by not waiting between updates of individual instances, aligning with the need to fix a critical vulnerability urgently without service disruption.

Links:

https://cloud.google.com/compute/docs/instance-groups/rolling-out-updates-to-managed-instance-groups#minimum_wait_time