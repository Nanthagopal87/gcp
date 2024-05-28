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


