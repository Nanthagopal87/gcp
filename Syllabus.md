### Section1: Designing highly scalable, available, and reliable cloud-native applications (~27% of the exam)

### Section 2: Building and testing applications (~20% of the exam)

### Section 3: Deploying applications (~18% of the exam)

### Section 4: Integrating Google Cloud services (~20% of the exam)

### Section 5: Managing deployed applications (~15% of the exam)

#

## Section 4: Integrating Google Cloud services (~20% of the exam)

4.1 Integrating an application with data and storage services. Considerations include:

- Managing connections to data stores (e.g., Cloud SQL, Cloud Spanner, Firestore, Bigtable, Cloud Storage)
- Reading/writing data to/from various data stores
- Writing an application that publishes/consumes data asynchronously (e.g., from Pub/Sub)

4.2 Integrating an application with compute services. Considerations include:
-  Using service discovery (e.g., Service Directory)
- Reading instance metadata to obtain application configuration
-  Graceful application startup and shutdown

4.3 Integrating Cloud APIs with applications. Considerations include:
- Enabling a Cloud API
-  Making API calls using supported options (e.g., Cloud Client Library, REST API or gRPC, API Explorer) taking into consideration:
   - Batching requests
   - Restricting return data
   - Paginating results
   - Caching results
   - Error handling (e.g., exponential backoff)
- Using service accounts to make Cloud API calls

## Section 5: Managing deployed applications (~15% of the exam)

5.1 Managing cloud compute services (e.g., Google Kubernetes Engine, serverless). Considerations include:
- Analyzing lifecycle events
- Using external metrics and corresponding alerts
- Configuring workload autoscaling

5.2 Troubleshooting applications. Considerations include:
- Using Debugger
- Using Cloud Logging
- Using Cloud Monitoring
- Using Cloud Profiler
- Using Cloud Trace
- Using Error Reporting
- Using documentation, forums, and Google Cloud support