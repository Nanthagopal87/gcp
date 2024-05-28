### 5. You are a developer at a large organization. You are deploying a web application to Google Kubernetes Engine (GKE). The DevOps team has built a CI/CD pipeline that uses Cloud Deploy to deploy the application to Dev, Test, and Prod clusters in GKE. After Cloud Deploy successfully deploys the application to the Dev cluster, you want to automatically promote it to the Test cluster.

How should you configure this process following Google-recommended best practices?

- A.

1. Create a Cloud Build trigger that listens for SUCCEEDED Pub/Sub messages from the clouddeploy-operations topic.

2. Configure Cloud Build to include a step that promotes the application to the Test cluster.

- B.

1. Create a Cloud Function that calls the Google Cloud Deploy API to promote the application to the Test cluster.

2. Configure this function to be triggered by SUCCEEDED Pub/Sub messages from the cloud-builds topic.

- C.

1. Create a Cloud Function that calls the Google Cloud Deploy API to promote the application to the Test cluster.

2. Configure this function to be triggered by SUCCEEDED Pub/Sub messages from the clouddeploy-operations topic.

- D.

1. Create a Cloud Build pipeline that uses the gke-deploy builder.

2. Create a Cloud Build trigger that listens for SUCCEEDED Pub/Sub messages from the cloud-builds topic.

3. Configure this pipeline to run a deployment step to the Test cluster.

### Ans: C
This option includes creating a Cloud Function that calls the Google Cloud Deploy API, which is suitable for promoting the application between environments in a CI/CD pipeline. It also correctly listens for SUCCEEDED Pub/Sub messages from the clouddeploy-operations topic, which is related to Cloud Deploy operations.

https://cloud.google.com/functions/docs/calling/pubsub

