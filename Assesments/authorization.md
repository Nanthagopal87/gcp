### 1. You developed a JavaScript web application that needs to access Google Drive's API and obtain permission from users to store files in their Google Drives. You need to select an authorization approach for your application.

What should you do?

- A. Create an API key.
- B. Create a SAML token.
- C. Create a service account.
- D. Create an OAuth Client ID.

### Ans: D


A. Create an API key.

API keys are used to identify the calling project (your application) to Google but are not suitable for handling user authorization and permissions. API keys don't provide user-level access control.

B. Create a SAML token.

SAML (Security Assertion Markup Language) is used for single sign-on (SSO) and doesn't apply in this context where individual user authorization for accessing Google Drive is required.

C. Create a service account.

Service accounts are used to authenticate and authorize applications, not individual users. If you were to use a service account, the application would be accessing Google Drive with its own identity, not on behalf of individual users.

D. Create an OAuth Client ID.

OAuth is specifically designed for authorizing third-party applications to access user resources without exposing the user's password. By creating an OAuth Client ID, you can redirect users to a Google-hosted page where they can grant the necessary permissions to your application.

https://developers.google.com/drive/api/guides/api-specific-auth


### 2. You have an application deployed in Google Kubernetes Engine (GKE). You need to update the application to make authorized requests to Google Cloud managed services. You want this to be a one-time setup, and you need to follow security best practices of auto-rotating your security keys and storing them in an encrypted store. You already created a service account with appropriate access to the Google Cloud service.

What should you do next?

- A. Assign the Google Cloud service account to your GKE Pod using Workload Identity.

- B. Export the Google Cloud service account, and share it with the Pod as a Kubernetes Secret.

- C. Export the Google Cloud service account, and embed it in the source code of the application.

- D. Export the Google Cloud service account, and upload it to HashiCorp Vault to generate a dynamic service account for your application.


### Ans: A

Incorrect Answers:

B. Export the Google Cloud service account, and share it with the Pod as a Kubernetes Secret.

Using Kubernetes Secrets to store service account keys does not provide automatic rotation, and it may pose a security risk if not handled correctly.

C. Export the Google Cloud service account, and embed it in the source code of the application.

Embedding the service account in the source code is a bad practice and poses significant security risks, as anyone with access to the source code would have access to the service account.

D. Export the Google Cloud service account, and upload it to HashiCorp Vault to generate a dynamic service account for your application.

HashiCorp Vault is a powerful tool for secrets management, but using Workload Identity is the more straightforward and recommended way to handle identity for GKE workloads interacting with Google Cloud services.



Correct Answer:

A. Assign the Google Cloud service account to your GKE Pod using Workload Identity.

Workload Identity is the recommended way to access Google Cloud services from within GKE. It lets you bind a Kubernetes service account to a Google service account, and this binding allows the Kubernetes service account to act as the Google service account. With Workload Identity, you don't have to manage service account keys, and they are auto-rotated, aligning with best practices.

Links:

https://cloud.google.com/kubernetes-engine/docs/concepts/workload-identity

