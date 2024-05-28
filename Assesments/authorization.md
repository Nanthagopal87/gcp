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

