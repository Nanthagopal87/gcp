### 1. Your web application is deployed to the corporate intranet. You need to migrate the web application to Google Cloud. The web application must be available only to company employees and accessible to employees as they travel. You need to ensure the security and accessibility of the web application while minimizing application changes.

What actions do you need to take?

- A. Configure the application to check authentication credentials for each HTTP(S) request to the application.

- B. Configure Identity-Aware Proxy to allow employees to access the application through its public IP address.

- C. Configure a Compute Engine instance that requests users to log in to their corporate account. Change the web application DNS to point to the proxy Compute Engine instance. After authenticating, the Compute Engine instance forwards requests to and from the web application.

- D. Configure a Compute Engine instance that requests users to log in to their corporate account. Change the web application DNS to point to the proxy Compute Engine instance. After authenticating, the Compute Engine issues an HTTP redirect to a public IP address hosting the web application.

### Ans: C

A. Configure the application to check authentication credentials for each HTTP(S) request to the application.

This option would likely require substantial changes to the application to implement the authentication check for every HTTP(S) request, which contradicts the requirement to minimize application changes.

B. Configure Identity-Aware Proxy to allow employees to access the application through its public IP address.

Identity-Aware Proxy (IAP) is a feature of the Google Cloud Platform that allows you to secure access to resources by using identity and context-based access control. IAP allows you to restrict access to a resource (such as a web application) to only authenticated and authorized users or service accounts.

However, in this scenario, since the web application is hosted on the corporate intranet, it will not have a public IP address, and it will not be accessible from the internet. Also, it's not possible to use IAP to restrict access to an intranet-hosted application by its IP address.

D. Configure a Compute Engine instance that requests users to log in to their corporate account. Change the web application DNS to point to the proxy Compute Engine instance. After authenticating, the Compute Engine issues an HTTP redirect to a public IP address hosting the web application.

These option involve configuring a Compute Engine instance to serve as a proxy and authenticate users through their corporate accounts. Also it includes an HTTP redirect to a public IP address hosting the web application, which may not align with the need to restrict access only to employees.

C. Configure a Compute Engine instance that requests users to log in to their corporate account. Change the web application DNS to point to the proxy Compute Engine instance. After authenticating, the Compute Engine instance forwards requests to and from the web application.

This approach enables the utilization of Google Cloud infrastructure to authenticate users through the corporate intranet before granting access to the web application, all without requiring major modifications to the web application itself. By setting up a Compute Engine instance to act as a proxy, and altering the web application's DNS to point to this proxy, access to the web application is limited solely to employees who have been authenticated against the corporate intranet. Additionally, this method permits employees to access the web application while traveling, provided they have access to the internet.

https://cloud.google.com/compute/docs
https://cloud.google.com/iam