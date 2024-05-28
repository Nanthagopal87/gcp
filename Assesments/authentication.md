### 1. You need to build a public API that authenticates, enforces quotas, and reports metrics for API callers.
Which tool should you use to complete this architecture?

- A. App Engine
- B. Cloud Endpoints
- C. Identity-Aware Proxy
- D. GKE Ingress for HTTP(S) Load Balancing

### Ans: B

A. App Engine

Cloud Run provides none of these features.

C. Identity-Aware Proxy

IAP provides only authentication.

D. GKE Ingress for HTTP(S) Load Balancing

GKE Ingress provides none of these features.



Correct Answer:

B. Cloud Endpoints

All three features, authentication, quotas/rate limiting and metrics are the core features of Cloud Endpoints.

Links:

https://cloud.google.com/endpoints/docs/openapi/quotas-configure

https://cloud.google.com/endpoints/docs/openapi/monitoring-your-api