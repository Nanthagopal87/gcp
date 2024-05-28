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