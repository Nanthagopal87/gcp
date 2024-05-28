### 1. You have two Google Cloud projects, named Project A and Project B. You need to create a Cloud Function in Project A that saves the output in a Cloud Storage bucket in Project B. You want to follow the principle of least privilege. What should you do?

What should you do?

- A.
1. Create a Google service account in Project B.

2. Deploy the Cloud Function with the service account in Project A.

3. Assign this service account the roles/storage.objectCreator role on the storage bucket residing in Project B.
- B.

1. Create a Google service account in Project A
2. Deploy the Cloud Function with the service account in Project A.
3. Assign this service account the roles/storage.objectCreator role on the storage bucket residing in Project B.


- C.
1. Determine the default App Engine service account (PROJECT_ID@appspot.gserviceaccount.com) in Project A.

2. Deploy the Cloud Function with the default App Engine service account in Project A.

3. Assign the default App Engine service account the roles/storage.objectCreator role on the storage bucket residing in Project B.

- D
1. Determine the default App Engine service account (PROJECT_ID@appspot.gserviceaccount.com) in Project B.

2. Deploy the Cloud Function with the default App Engine service account in Project A.

3. Assign the default App Engine service account the roles/storage.objectCreator role on the storage bucket residing in Project B.

### ANS: B

### 2. You have two tables in an ANSI-SQL compliant database with identical columns that you need to quickly combine into a single table, removing duplicate rows from the result set.

- A. Grant your user account the roles/storage.objectCreator role for the Cloud Storage bucket.
- B. Grant your user account the roles/iam.serviceAccountUser role for the service-PROJECTA@gcf-admin-robot.iam.gserviceaccount.com service account.
- C. Grant the service-PROJECTA@gcf-admin-robot.iam.gserviceaccount.com service account the roles/storage.objectCreator role for the Cloud Storage bucket.
- D. Enable the Cloud Storage API in project B.

### Ans: C
When running code on Cloud Functions, the code executes with the permissions of the service account associated with the function. In this case, the error "403 Forbidden" is typically indicative of a permission issue related to the service account trying to write to the Cloud Storage bucket.

Since the code is running on Cloud Functions in project A and is supposed to write an object in a Cloud Storage bucket owned by project B, you should grant the appropriate permissions to the service account associated with the Cloud Functions instance (service-PROJECTA@gcf-admin-robot.iam.gserviceaccount.com) for the Cloud Storage bucket in project B.

https://cloud.google.com/functions/docs/concepts/iam#troubleshooting_permission_errors

### 3. Your team develops services that run on Google Cloud. You need to build a data processing service and will use Cloud Functions. The data to be processed by the function is sensitive. You need to ensure that invocations can only happen from authorized services and follow Google-recommended best practices for securing functions.

What should you do?

- A. Enable Identity-Aware Proxy in your project. Secure function access using its permissions.
- B. Create a service account with the Cloud Functions Viewer role. Use that service account to invoke the function.
- C. Create a service account with the Cloud Functions Invoker role. Use that service account to invoke the function.
- D. Create an OAuth 2.0 client ID for your calling service in the same project as the function you want to secure. Use those credentials to invoke the function.

### Ans: C
For securing Cloud Functions and ensuring that only authorized services can invoke them, following Google-recommended best practices, you would want to create a service account with a role that allows the invocation of the function and use that service account to make the calls.

https://cloud.google.com/functions/docs/securing/authenticating#authenticating_function_to_function_calls

### 4. Your development team has built several Cloud Functions using Java along with corresponding integration and service tests. You are building and deploying the functions and launching the tests using Cloud Build. Your Cloud Build job is reporting deployment failures immediately after successfully validating the code.

What should you do?

- A. Check the maximum number of Cloud Function instances.

- B. Verify that your Cloud Build trigger has the correct build parameters.

- C. Retry the tests using the truncated exponential backoff polling strategy.

- D. Verify that the Cloud Build service account is assigned the Cloud Functions Developer role.

### Ans: D

The Cloud Functions Developer role would provide the necessary permissions to deploy Cloud Functions, and if the Cloud Build service account doesn't have this role, deployment failures could occur.

Therefore, the correct action to resolve deployment failures would be to verify and ensure that the Cloud Build service account has the necessary role to deploy Cloud Functions, as described in option D.

https://cloud.google.com/build/docs/troubleshooting#build_trigger_fails_due_to_missing_cloudbuildbuildscreate_permission



