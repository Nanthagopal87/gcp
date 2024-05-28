### 1. You are using the Cloud Client Library to upload an image in your application to Cloud Storage. Users of the application report that occasionally the upload does not complete and the client library reports an HTTP 504 Gateway Timeout error. You want to make the application more resilient to errors.

What changes to the application should you make?

- A. Write an exponential backoff process around the client library call.

- B. Write a one-second wait time backoff process around the client library call.

- C. Design a retry button in the application and ask users to click if the error occurs.

- D. Create a queue for the object and inform the users that the application will try again in 10 minutes.

### Ans: A

An exponential backoff strategy gradually increases the time between retries, reducing the load on the system and giving the failing component more time to recover. This approach is often recommended by cloud providers to handle transient errors, making this the best option.

https://cloud.google.com/storage/docs/retry-strategy#exponential-backoff

