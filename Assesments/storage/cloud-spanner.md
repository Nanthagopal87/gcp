### 1. You recently joined a new team that has a Cloud Spanner database instance running in production. Your manager has asked you to optimize the Spanner instance to reduce cost while maintaining high reliability and availability of the database.

What should you do?

- A. Use Cloud Logging to check for error logs, and reduce Spanner processing units by small increments until you find the minimum capacity required.
- B. Use Cloud Monitoring to monitor the CPU utilization, and reduce Spanner processing units by small increments until you find the minimum capacity required.
- C. Use Cloud Trace to monitor the requests per sec of incoming requests to Spanner, and reduce Spanner processing units by small increments until you find the minimum capacity required.
- D. Use Snapshot Debugger to check for application errors, and reduce Spanner processing units by small increments until you find the minimum capacity required.

To optimize a Cloud Spanner database instance for cost while maintaining high reliability and availability, you'll need to find the balance between processing units and the actual demand of your system. Cloud Spanner's CPU utilization metrics can be a key indicator to understand the capacity requirements.

Option B, "Use Cloud Monitoring to monitor the CPU utilization, and reduce Spanner processing units by small increments until you find the minimum capacity required," is the correct approach.

Links:

https://cloud.google.com/spanner/docs/compute-capacity#increasing_and_decreasing_compute_capacity

### 2. You are working on an application that relies on Cloud Spanner as its primary datastore. New application features have, on occasion, caused performance regressions. To prevent performance issues, you want to run an automated performance test with Cloud Build for each commit made. If multiple commits are made simultaneously, the tests may run concurrently.

What should you do?

- A. Create a new project with a random name for each build, load the necessary data, and delete the project after the test is completed.

- B. Create a new Cloud Spanner instance for each build, load the required data, and delete the Cloud Spanner instance after the test is completed.

- C. Set up a project with a Cloud Spanner instance and the required data, and modify the Cloud Build build file to automatically restore the data to its previous state after the test is completed.

- D. Launch the Cloud Spanner emulator locally, load the necessary data, and shut down the emulator after the test is completed.

### Ans: B

A. Create a new project with a random name for each build, load the necessary data, and delete the project after the test is completed.

This approach ensures complete isolation for each test by using separate projects. It avoids any interference between concurrent tests and provides a clean environment for each run. However, creating and deleting a project for each build can be time-consuming and may lead to increased operational complexity and costs.

C. Set up a project with a Cloud Spanner instance and the required data, and modify the Cloud Build build file to automatically restore the data to its previous state after the test is completed.

This option uses a single Cloud Spanner instance and relies on restoring data to its original state after each test. While this method is efficient in terms of resource utilization, it may not handle concurrent tests effectively. Concurrent tests could interfere with each other, especially if they are modifying the same data, leading to unreliable test results.

D. Launch the Cloud Spanner emulator locally, load the necessary data, and shut down the emulator after the test is completed.

The Cloud Spanner emulator provides a local environment for development and testing, eliminating the need to create and manage cloud resources. This approach supports concurrent testing, as each test can launch its own emulator instance. It is also cost-effective since the emulator runs locally. However, the emulator may not fully replicate the performance characteristics of the actual Cloud Spanner service, which could limit the accuracy of performance tests.

Correct answer:

B. Create a new Cloud Spanner instance for each build, load the required data, and delete the Cloud Spanner instance after the test is completed.

Creating a new Cloud Spanner instance for each build provides isolation at the database level, allowing concurrent tests to run without affecting each other. This method is more efficient than creating a whole new project and reduces the overhead associated with project management. However, it still involves creating and deleting resources, which can be time-consuming and may incur costs.

Links:

https://cloud.google.com/spanner/docs/emulator#limitations

### 3. You are developing an ecommerce application that stores customer, order, and inventory data as relational tables inside Cloud Spanner. During a recent load test, you discover that Spanner performance is not scaling linearly as expected.

Which of the following is the cause?

- A. The use of 64-bit numeric types for 32-bit numbers.

- B. The use of Version 1 UUIDs as primary keys that increase monotonically.

- C. The use of the STRING data type for arbitrary-precision values.

- D. The use of LIKE instead of STARTS_WITH keyword for parameterized SQL queries.

A. The use of 64-bit numeric types for 32-bit numbers.

While this may be less efficient in terms of storage, it's unlikely to have a significant impact on Spanner's linear scaling capabilities.

C. The use of the STRING data type for arbitrary-precision values.

While using the STRING data type for arbitrary-precision values might not be the optimal choice, it should not substantially affect linear scaling.

D. The use of LIKE instead of STARTS_WITH keyword for parameterized SQL queries.

This could affect query performance, but it would not typically affect the linear scaling of the overall system.



Correct Answer:

B. The use of Version 1 UUIDs as primary keys that increase monotonically.

In Cloud Spanner, the use of Version 1 UUIDs as primary keys that increase monotonically can cause performance issues because they are not evenly distributed. This can lead to hot regions, where a disproportionate number of requests are sent to a specific node or range of nodes, causing those nodes to become overloaded and leading to decreased performance. To improve performance, you should consider using primary keys that are more evenly distributed, such as hash-based keys or random integers.



Links:

https://cloud.google.com/spanner/docs/schema-and-data-model#choosing_a_primary_key

https://cloud.google.com/spanner/docs/schema-design#primary-key-prevent-hotspots

### 4. You are writing from a Go application to a Cloud Spanner database. You want to optimize your application’s performance using Google-recommended best practices.

What should you do?

- A. Write to Cloud Spanner using Cloud Client Libraries.

- B. Write to Cloud Spanner using Google API Client Libraries

- C. Write to Cloud Spanner using a custom gRPC client library.

- D. Write to Cloud Spanner using a third-party HTTP client library.

### Ans: A

ncorrect Answers:

B. Write to Cloud Spanner using Google API Client Libraries

While this is technically possible, Cloud Client Libraries are preferred as they are specifically tailored to the service, making development easier and more efficient.

C. Write to Cloud Spanner using a custom gRPC client library.

Creating a custom gRPC client library is likely to be more error-prone and time-consuming compared to using the officially supported libraries.

D. Write to Cloud Spanner using a third-party HTTP client library.

Relying on third-party libraries can introduce compatibility and support risks, and may not be optimized for Cloud Spanner.



Correct Answer:

A. Write to Cloud Spanner using Cloud Client Libraries.

When working with Cloud Spanner from a Go application, Google recommends using Cloud Client Libraries, which are idiomatic and optimized for the service. These libraries make it easier to integrate with Google Cloud services, providing a higher-level, more convenient abstraction over Google API Client Libraries.

So Option A is the recommended approach as it provides an idiomatic and optimized way to work with Cloud Spanner from Go.



Links:

https://cloud.google.com/apis/docs/client-libraries-explained

https://cloud.google.com/go/docs/reference
