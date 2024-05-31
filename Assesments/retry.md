### 1. You support an application that uses the Cloud Storage API. You review the logs and discover multiple HTTP 503 Service Unavailable error responses from the API. Your application logs the error and does not take any further action. You want to implement Google-recommended retry logic to improve success rates.

Which approach should you take?

- A. Retry the failures in batch after a set number of failures is logged.

- B. Retry each failure at a set time interval up to a maximum number of times.

- C. Retry each failure at increasing time intervals up to a maximum number of tries.

- D. Retry each failure at decreasing time intervals up to a maximum number of tries.

### Ans: C

Incorrect Answers:

A. Retry the failures in batch after a set number of failures is logged.

This approach doesn't consider the transient nature of 503 errors and could lead to all retries happening at once, potentially exacerbating the issue.

B. Retry each failure at a set time interval up to a maximum number of times.

This method does not adapt to the situation and could continue to put load on an already struggling service.

D. Retry each failure at decreasing time intervals up to a maximum number of tries.

Decreasing the time between retries is likely to increase the load on the struggling service, making the situation worse rather than helping.



Correct Answer:

C. Retry each failure at increasing time intervals up to a maximum number of tries.

Is the best practice in this scenario because it helps mitigate the risk of overwhelming a system that's already experiencing issues, allowing it time to recover between each retry attempt.



Links:

https://cloud.google.com/storage/docs/retry-strategy