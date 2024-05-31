### 1. You are using the Cloud Client Library to upload an image in your application to Cloud Storage. Users of the application report that occasionally the upload does not complete and the client library reports an HTTP 504 Gateway Timeout error. You want to make the application more resilient to errors.

What changes to the application should you make?

- A. Write an exponential backoff process around the client library call.

- B. Write a one-second wait time backoff process around the client library call.

- C. Design a retry button in the application and ask users to click if the error occurs.

- D. Create a queue for the object and inform the users that the application will try again in 10 minutes.

### Ans: A

An exponential backoff strategy gradually increases the time between retries, reducing the load on the system and giving the failing component more time to recover. This approach is often recommended by cloud providers to handle transient errors, making this the best option.

https://cloud.google.com/storage/docs/retry-strategy#exponential-backoff

### 2. You are in the process of developing a new application that should activate exclusively when a specific file in your Cloud Storage bucket is updated. The nature of your project requires flexibility in trigger mechanisms, as the type of trigger may vary over time. Additionally, it's important for the configuration process to be straightforward, enabling various team members to easily modify triggers in the future.

What steps should you take to achieve this?

- A. Configure Cloud Storage events to be sent to Pub/Sub, and use Pub/Sub events to trigger a Cloud Build job that executes your application.

- B. Create an Eventarc trigger that monitors your Cloud Storage bucket for a specific filename, and set the target as Cloud Run.

- C. Configure a Cloud Function that executes your application and is triggered when an object is updated in Cloud Storage.

- D. Configure a Firebase function that executes your application and is triggered when an object is updated in Cloud Storage.

### Ans: C

ncorrect Answers:

A. Configure Cloud Storage events to be sent to Pub/Sub, and use Pub/Sub events to trigger a Cloud Build job that executes your application.

While this method could work, it's more complex and less direct compared to using Cloud Functions. It involves multiple steps and services, which might not be ideal for simplicity and ease of future modifications.

B. Create an Eventarc trigger that monitors your Cloud Storage bucket for a specific filename, and set the target as Cloud Run.

This option is also viable and offers flexibility. However, Cloud Run is typically used for containerized applications and might be more complex to set up and manage compared to a Cloud Function.

D. Configure a Firebase function that executes your application and is triggered when an object is updated in Cloud Storage.

Firebase Functions are similar to Cloud Functions, but they are more integrated with Firebase services. If your application is not using Firebase extensively, this option might add unnecessary complexity.



Correct Answer:

C. Configure a Cloud Function that executes your application and is triggered when an object is updated in Cloud Storage.

This is the most straightforward option. Cloud Functions are designed to respond to cloud events in a lightweight and efficient manner. It's easy to set up and manage, making it a good fit for teams who might need to update triggers in the future.



Link:

Cloud Functions triggers
https://cloud.google.com/functions/docs/calling

Cloud Storage triggers
https://cloud.google.com/functions/docs/calling/storage

Invoke Cloud Functions or Cloud Run
https://cloud.google.com/workflows/docs/calling-run-functions#:~:text=Calling%20or%20invoking%20a%20Google,the%20call%20field%20to%20http.


### 3. Your data is stored in Cloud Storage buckets.

Fellow developers have reported that data downloaded from Cloud Storage is resulting in slow API performance. You want to research the issue to provide details to the Google Cloud support team.

Which command should you run?

- A. gsutil test -o output.json gs://my-bucket

- B. gsutil perfdiag -o output.json gs://my-bucket

- C. gcloud compute scp example-instance:~/test-data -o output.json gs://my-bucket

- D. gcloud services test -o output.json gs://my-bucket

### Ans: B

Incorrect Answers:

A. gsutil test -o output.json gs://my-bucket

This command does not exist in the gsutil command-line tool, and the option "test" is not recognized, so it won't execute properly.

C. gcloud compute scp example-instance:~/test-data -o output.json gs://my-bucket

The gcloud compute scp command is used to copy files between a local machine and a virtual machine, or between two virtual machines. It's not related to diagnosing performance issues with Cloud Storage, so it's not applicable to the task at hand.

D. gcloud services test -o output.json gs://my-bucket

This command doesn't exist in the gcloud command-line tool. There is no "test" command under gcloud services, so this line would result in an error.



Correct Answer:

B. gsutil perfdiag -o output.json gs://my-bucket

The gsutil perfdiag command can be used to diagnose performance issues with Google Cloud Storage. It runs a suite of diagnostic tests and collects information that might help to identify what's causing performance problems.



Links:

https://cloud.google.com/storage/docs/gsutil/commands/perfdiag#providing-diagnostic-output-to-cloud-storage-team
