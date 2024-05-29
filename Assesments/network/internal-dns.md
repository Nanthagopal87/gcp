### 1. You are developing an HTTP API hosted on a Compute Engine virtual machine instance that needs to be invoked by multiple clients within the same VPC (Virtual Private Cloud). You want clients to be able to get the IP address of the service.

What should you do?

- A. Reserve a static external IP address and assign it to an HTTP(S) load balancing service's forwarding rule. Clients should use this IP address to connect to the service.

- B. Reserve a static external IP address and assign it to an HTTP(S) load balancing service's forwarding rule. Then, define an A record in Cloud DNS. Clients should use the name of the A record to connect to the service.

- C. Ensure that clients use Compute Engine internal DNS by connecting to the instance name with the URL https://[INSTANCE_NAME].[ZONE].c.[PROJECT_ID].internal/.

- D. Ensure that clients use Compute Engine internal DNS by connecting to the instance name with the URL https://[API_NAME]/[API_VERSION]/.

### Ans: C

A. Reserve a static external IP address and assign it to an HTTP(S) load balancing service's forwarding rule. Clients should use this IP address to connect to the service.

The static external IP address provides a fixed IP address that clients can use to connect to the service. This is important because the IP address of the instance can change if the instance is restarted or if the instance is part of an auto-scaling group.

The HTTP(S) load balancing service allows for traffic to be distributed across multiple instances, which can provide better performance and availability for the service. It can also handle health checks to automatically remove unhealthy instances from the pool of available instances.

By using a forwarding rule, traffic can be directed to the correct instance based on the URL or IP address. This allows multiple services to be hosted on a single IP address and port combination.

Clients can connect to the service using the IP address assigned to the forwarding rule.

In conclusion this complexity solution can be marked as “non-optimal”

B. Reserve a static external IP address and assign it to an HTTP(S) load balancing service's forwarding rule. Then, define an A record in Cloud DNS. Clients should use the name of the A record to connect to the service.

Explanation:

This option is similar to option A, but instead of using the IP address to connect to the service, clients would use the name of the A record defined in Cloud DNS. This can provide a more user-friendly name for the service, but it also adds additional complexity to the setup.

Additionally, using Cloud DNS adds another service that needs to be configured and managed, which can increase the potential for issues and downtime.

D. Ensure that clients use Compute Engine internal DNS by connecting to the instance name with the URL https://[API_NAME]/[API_VERSION]/.

Explanation:

This option is similar to option C, but instead of using the instance name in the URL, it uses an API name and version. This can provide a more user-friendly URL, but it still relies on the internal DNS service provided by Compute Engine.

Using a custom API name and version can also add additional complexity to the setup and may require additional configuration and management.

C. Ensure that clients use Compute Engine internal DNS by connecting to the instance name with the URL https://[INSTANCE_NAME].[ZONE].c.[PROJECT_ID].internal/.

This option uses the internal DNS service provided by Compute Engine to resolve the IP address of the instance hosting the service. This can work if all clients are within the same VPC and have access to the internal DNS service, which is true for the current question.

In summary, the best option for allowing clients within the same VPC to get the IP address of the HTTP API hosted on a Compute Engine virtual machine instance would be to ensure that clients use Compute Engine internal DNS by connecting to the instance name with the URL https://[INSTANCE_NAME].[ZONE].c.[PROJECT_ID].internal/

https://cloud.google.com/compute/docs/internal-dns

