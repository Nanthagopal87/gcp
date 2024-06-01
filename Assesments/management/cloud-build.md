### 1. You work for a web development team at a small startup. Your team is developing a Node.js application using Google Cloud services, including Cloud Storage and Cloud Build. The team uses a Git repository for version control. Your manager calls you over the weekend and instructs you to make an emergency update to one of the company's websites, and you're the only developer available. You need to access Google Cloud to make the update, but you don't have your work laptop. You are not allowed to store source code locally on a non-corporate computer.

How should you set up your developer environment?

- A. Use a text editor and the Git command line to send your source code updates as pull requests from a public computer.
- B. Use a text editor and the Git command line to send your source code updates as pull requests from a virtual machine running on a public computer.
- C. Use Cloud Shell and the built-in code editor for development. Send your source code updates as pull requests.
- D. Use a Cloud Storage bucket to store the source code that you need to edit. Mount the bucket to a public computer as a drive, and use a code editor to update the code. Turn on versioning for the bucket, and point it to the team's Git repository.

### Ans: C

### 2. You are using Cloud Build to build and test application source code stored in Cloud Source Repositories. The build process requires a build tool not available in the Cloud Build environment.
What should you do?

- A. Download the binary from the internet during the build process.

- B. Build a custom cloud builder image and reference the image in your build steps.

- C. Include the binary in your Cloud Source Repositories repository and reference it in your build scripts.

- D. Ask to have the binary added to the Cloud Build environment by filing a feature request against the Cloud Build public Issue Tracker.

### Ans: B


### 3. You work for a financial services company that has a container-first approach. Your team develops microservices applications. A Cloud Build pipeline creates the container image, runs regression tests, and publishes the image to Artifact Registry. You need to ensure that only containers that have passed the regression tests are deployed to Google Kubernetes Engine (GKE) clusters. You have already enabled Binary Authorization on the GKE clusters.

What should you do next?

- A. Create an attestor and a policy. After a container image has successfully passed the regression tests, use Cloud Build to run Kritis Signer to create an attestation for the container image.
- B. Deploy Voucher Server and Voucher Client components. After a container image has successfully passed the regression tests, run Voucher Client as a step in the Cloud Build pipeline.
- C. Set the Pod Security Standard level to Restricted for the relevant namespaces. Use Cloud Build to digitally sign the container images that have passed the regression tests.
- D. Create an attestor and a policy. Create an attestation for the container images that have passed the regression tests as a step in the Cloud Build pipeline.

### Ans: A

Involves creating an attestor and a policy, then using Cloud Build to run Kritis Signer to create an attestation for the container image that passed the regression tests. Kritis Signer is part of the Grafeas project and integrates with Binary Authorization.

Among these options, Option A is the most suitable. It includes all the necessary steps: creating an attestor, setting a policy, and creating an attestation using a tool (Kritis Signer) that is designed to work with Binary Authorization.

https://cloud.google.com/binary-authorization/docs/creating-attestations-kritis

### 4. You are building a CI/CD pipeline that consists of a version control system, Cloud Build, and Container Registry. Each time a new tag is pushed to the repository, a Cloud Build job is triggered, which runs unit tests on the new code, builds a new Docker container image, and pushes it into Container Registry. The last step of your pipeline should deploy the new container to your production Google Kubernetes Engine (GKE) cluster. You need to select a tool and deployment strategy that meets the following requirements:

Zero downtime is incurred

Testing is fully automated

Allows for testing before being rolled out to users

Can quickly rollback if needed

What should you do?

- A. Trigger a Spinnaker pipeline configured as an A/B test of your new code, and, if it is successful, deploy the container to production.
- B. Trigger a Spinnaker pipeline configured as a canary test of your new code, and, if it is successful, deploy the container to production.
- C. Trigger another Cloud Build job that uses the Kubernetes CLI tools to deploy your new container to your GKE cluster, where you can perform a canary test.
- D. Trigger another Cloud Build job that uses the Kubernetes CLI tools to deploy your new container to your GKE cluster, where you can perform a shadow test.

### Ans: D

Shadow testing involves deploying the new version alongside the old without affecting the actual users. All requests to the old version are duplicated to the new one, but the results from the new version are discarded. This allows you to observe how the new version would behave in the live environment without affecting users.

https://cloud.google.com/architecture/implementing-deployment-and-testing-strategies-on-gke#perform_a_shadow_test

### 5. Your company stores their source code in a Cloud Source Repositories repository. Your company wants to build and test their code on each source code commit to the repository and requires a solution that is managed and has minimal operations overhead.

Which method should they use?

- A. Use Cloud Build with a trigger configured for each source code commit.
- B. Use Jenkins deployed via the Google Cloud Platform Marketplace, configured to watch for source code commits.

- C. Use a Compute Engine virtual machine instance with an open source continuous integration tool, configured to watch for source code commits.

D. Use a source code commit trigger to push a message to a Cloud Pub/Sub topic that triggers an App Engine service to build the source code.

### Ans: A

Option A is the simplest and most straightforward approach, using Google Cloud's managed continuous integration and continuous delivery platform. Cloud Build can be easily configured to automatically build and test the code on each source code commit, and it aligns well with the requirements for a managed solution with minimal operational overhead.

https://cloud.google.com/build/docs/automating-builds/create-manage-triggers


### 6. Your company's development teams want to use Cloud Build in their projects to build and push Docker images to Container Registry. The operations team requires all Docker images to be published to a centralized, securely managed Docker registry that the operations team manages.

What should you do?

- A.

Use Container Registry to create a registry in each development team's project.

Configure the Cloud Build build to push the Docker image to the project's registry.

Grant the operations team access to each development team's registry.

- B.

Create a separate project for the operations team that has Container Registry configured.

Assign appropriate permissions to the Cloud Build service account in each developer team's project to allow access to the operation team's registry.

- C.

Create a separate project for the operations team that has Container Registry configured.

Create a Service Account for each development team and assign the appropriate permissions to allow it access to the operations team's registry.

Store the service account key file in the source code repository and use it to authenticate against the operations team's registry.

- D.

Create a separate project for the operations team that has the open source Docker Registry deployed on a Compute Engine virtual machine instance.

Create a username and password for each development team.

Store the username and password in the source code repository and use it to authenticate against the operations team's Docker registry.

### Ans: B

ncorrect Answers:

A.

Use Container Registry to create a registry in each development team's project.

Configure the Cloud Build build to push the Docker image to the project's registry.

Grant the operations team access to each development team's registry.

C.

Create a separate project for the operations team that has Container Registry configured.

Create a Service Account for each development team and assign the appropriate permissions to allow it access to the operations team's registry.

Store the service account key file in the source code repository and use it to authenticate against the operations team's registry.

D.

Create a separate project for the operations team that has the open source Docker Registry deployed on a Compute Engine virtual machine instance.

Create a username and password for each development team.

Store the username and password in the source code repository and use it to authenticate against the operations team's Docker registry.

Option A: Is not ideal because it requires granting the operations team access to each development team's registry, which may not be secure.

Option C: It is not the best choice because it requires storing the service account key file in the source code repository, which may not be secure.

Option D: This is not the best choice because it requires using an open-source Docker Registry and creating a username and password for each development team, which may not be secure or efficient.



Correct Answer:

B.

Create a separate project for the operations team that has Container Registry configured.

Assign appropriate permissions to the Cloud Build service account in each developer team's project to allow access to the operation team's registry.

B is the best choice because it allows the operations team to have control over the centralized, securely managed Docker registry while also enabling the development teams to use Cloud Build in their projects. In this option, the operations team can create a separate project with Container Registry configured and grant appropriate permissions to the Cloud Build service account in each development team's project, allowing access to the operations team's registry. This approach enables the development teams to build and push Docker images to the centralized registry while still adhering to the operations team's requirements.



Links:

https://cloud.google.com/container-registry/

https://stackoverflow.com/questions/48602546/google-cloud-functions-how-to-securely-store-service-account-private-key-when

### 7. You are developing a new web application using Cloud Run and committing code to Cloud Source Repositories. You want to deploy new code in the most efficient way possible. You have already created a Cloud Build YAML file that builds a container and runs the following command: gcloud run deploy.

What should you do next?

- A. Create a Pub/Sub topic to be notified when code is pushed to the repository. Create a Pub/Sub trigger that runs the build file when an event is published to the topic.

- B. Create a build trigger that runs the build file in response to a repository code being pushed to the development branch.

- C. Create a webhook build trigger that runs the build file in response to HTTP POST calls to the webhook URL.

- D. Create a Cron job that runs the following command every 24 hours: gcloud builds submit.

### Ans: B

Incorrect Answers:

A. Create a Pub/Sub topic to be notified when code is pushed to the repository. Create a Pub/Sub trigger that runs the build file when an event is published to the topic.

Pub/Sub notifications are typically used for event-driven, asynchronous workloads, and not specifically for triggering builds.

C. Create a webhook build trigger that runs the build file in response to HTTP POST calls to the webhook URL.

is incorrect because while you can use webhooks to trigger builds, it's less efficient and less secure than using Cloud Build's native triggering mechanism. It would also involve more manual intervention or additional service configurations to send HTTP POST calls every time code is pushed to the repository.

D. Create a Cron job that runs the following command every 24 hours: gcloud builds submit.

It relies on a periodic (daily) build rather than reacting to code pushes. This is less efficient because it could result in unnecessary builds if no code changes have occurred, or it could delay the deployment of critical code changes.



Correct Answer:

B. Create a build trigger that runs the build file in response to a repository code being pushed to the development branch.

Cloud Build provides build triggers, which can be configured to run a build process when new code is pushed to a specified branch in your source code repository. This strategy is often called Continuous Deployment or Continuous Delivery. Option B allows you to automate the deployment process efficiently. Whenever a new code is pushed to the development branch, a build is triggered automatically, ensuring that changes are deployed promptly and only when needed.

Links:

https://cloud.google.com/build/docs/automating-builds/create-manage-triggers#connect_repo

### 8. You are developing a new application that has the following design requirements:

Creation and changes to the application infrastructure are versioned and auditable.

The application and deployment infrastructure uses Google-managed services as much as possible.

The application runs on a serverless compute platform.

How should you design the application's architecture?

- A.

1) Store the application and infrastructure source code in a Git repository.

2) Use Cloud Build to deploy the application infrastructure with Terraform.

3) Deploy the application to a Cloud Function as a pipeline step.

- B.

1) Deploy Jenkins from the Google Cloud Marketplace, and define a continuous integration pipeline in Jenkins.

2) Configure a pipeline step to pull the application source code from a Git repository.

3) Deploy the application source code to App Engine as a pipeline step.

- C.

1) Create a continuous integration pipeline on Cloud Build, and configure the pipeline to deploy the application infrastructure using Deployment Manager templates.

2) Configure a pipeline step to create a container with the latest application source code.

3) Deploy the container to a Compute Engine instance as a pipeline step.

- D.

1) Deploy the application infrastructure using gcloud commands.

2) Use Cloud Build to define a continuous integration pipeline for changes to the application source code.

3) Configure a pipeline step to pull the application source code from a Git repository, and create a containerized application.

4) Deploy the new container on Cloud Run as a pipeline step.

### Ans: D

ncorrect Answers:



Options A, B, C

The other options have elements that don't align with all the requirements. For example, Terraform in option A is not a Google-managed service, Jenkins in option B is not a Google-managed service, and Compute Engine in option C is not a serverless platform.



Correct Answer:

Option D:

Deploying the application infrastructure using gcloud commands:

This uses Google's command-line tool to manage resources, enabling versioning and auditability.

Using Cloud Build for a continuous integration pipeline:

Cloud Build is a Google-managed service that lets you build, test, and deploy applications on Google's infrastructure.

Pulling the application source code from a Git repository and creating a containerized application:

This fits the requirement of versioning and making use of containers.

Deploying the new container on Cloud Run as a pipeline step:

Cloud Run is a Google-managed serverless platform, which meets the requirement for running on a serverless compute platform.

Links:

https://cloud.google.com/docs/ci-cd

### 9. You have written a Cloud Function in Node.js with source code stored in a Git repository. You want any committed changes to the source code to be automatically tested. You write a Cloud Build configuration that pushes the source code to a uniquely named Cloud Function, then calls the function as a test, and then deletes the Cloud Function as cleanup. You discover that if the test fails, the Cloud Function is not deleted.

What should you do?

- A. Change the order of the steps to delete the Cloud Function before performing the test.

- B. Include a waitFor option in the Cloud Build step that deletes the Cloud Function test step as a required preceding step.

- C. Have the Cloud Build step write the Cloud Function results to a file and return 0. Add a step after the Cloud Function deletion that checks whether the file contains the expected results and fails if it doesn't.

- D. Have the Cloud Build test step set its outcome in an environment variable called result and return 0. Add a final step after the Cloud Function deletion that checks whether the environment variable contains the expected results.

### Ans: C

Incorrect Answers:

A. Change the order of the steps to delete the Cloud Function before performing the test.

Deleting the Cloud Function before performing the test would make the test impossible since the function would no longer exist.

B. Include a waitFor option in the Cloud Build step that deletes the Cloud Function test step as a required preceding step.

Using the waitFor option in this manner would cause the entire build to fail if the test fails, and the Cloud Function would not be deleted. It won't solve the issue of cleaning up the function if the test fails.

D. Have the Cloud Build test step set its outcome in an environment variable called result and return 0. Add a final step after the Cloud Function deletion that checks whether the environment variable contains the expected results.

Since environment variables are local to the container in which a step executes, they cannot be used to pass information between different steps in the build process.



Correct Answer:

C. Have the Cloud Build step write the Cloud Function results to a file and return 0. Add a step after the Cloud Function deletion that checks whether the file contains the expected results and fails if it doesn't.

By deploying the Cloud Function, saving the results to a file (regardless of success or failure), deleting the Cloud Function, and then testing the content of the file, you ensure proper cleanup and accurate reporting of the test results.

Links:

https://cloud.google.com/build/docs/configuring-builds/configure-build-step-order

https://cloud.google.com/build/docs/configuring-builds/create-basic-configuration

https://cloud.google.com/build/docs/build-config

### 10. 