### 1. You need to migrate an internal file upload API with an enforced 500-MB file size limit to App Engine.

What should you do?

- A. Use FTP to upload files.

- B. Use CPanel to upload files.

- C. Use signed URLs to upload files.

- D. Change the API to be a multipart file upload API.

### Ans: C

Incorrect Answers:

A. Use FTP to upload files.

B. Use CPanel to upload files.

D. Change the API to be a multipart file upload API.

Option A (FTP) doesn't align with typical practices in cloud environments like App Engine.

Option B (CPanel) is not related to handling file uploads programmatically.

Option D (multipart file upload API) might be a possible solution but doesn't specifically deal with the stated file size limit or the App Engine environment.



Correct Answer:

C. Use signed URLs to upload files.

Option C, using signed URLs to upload files, is the best approach among these choices. Signed URLs provide a secure and efficient way to handle file uploads, particularly when dealing with large files. They allow you to give users temporary access to a specific cloud resource, in this case, the ability to upload a file. Google Cloud Storage supports signed URLs, and they can be used in conjunction with App Engine to handle file uploads. By creating a signed URL, you can permit a client to upload a file directly to a bucket in Cloud Storage without having to handle the file on your App Engine server, thus abiding by the file size limits imposed by the App Engine environment.

Therefore, the correct answer is: C



Links:

https://cloud.google.com/storage/docs/access-control/signed-urls

https://cloud.google.com/appengine/docs/standard/php/googlestorage/user_upload

### 2. You have an application running in App Engine.

Your application is instrumented with Cloud Trace(formerly Stackdriver). The /product-details request reports details about four known unique products at /sku-details as shown below. You want to reduce the time it takes for the request to complete.

What should you do?

- A. Increase the size of the instance class.

- B. Change the Persistent Disk type to SSD.

- C. Change /product-details to perform the requests in parallel.

- D. Store the /sku-details information in a database, and replace the webservice call with a database query.

Incorrect Answers:

A. Increase the size of the instance class.

Increasing the size of the instance class may provide more resources, but it wouldn't necessarily address the core issue of sequential request handling.

B. Change the Persistent Disk type to SSD.

Changing the Persistent Disk type to SSD might enhance disk I/O performance, but the issue described here is related to network requests, not disk operations.

D. Store the /sku-details information in a database, and replace the webservice call with a database query.

Storing the /sku-details information in a database may improve performance in some scenarios, but it doesn't necessarily align with the problem described. If the /sku-details data changes frequently and is maintained by a third party, then database storage might not be suitable, and the problem could be solved more directly by parallelizing the requests.



Correct Answer:

C. Change /product-details to perform the requests in parallel.

By making the requests in parallel, you can reduce the time it takes for the overall /product-details request to complete.



Links:

https://cloud.google.com/appengine/docs/standard/java/datastore/queries

### 3. Your App Engine standard configuration is as follows:

- service: production

- instance_class: B1

You want to limit the application to 5 instances.

Which code snippet should you include in your configuration?

- A. manual_scaling:

instances: 5 min_pending_latency: 30ms

- B. manual_scaling:

max_instances: 5 idle_timeout: 10m

- C. basic_scaling:

instances: 5 min_pending_latency: 30ms

- D. basic_scaling:

max_instances: 5 idle_timeout: 10m

### Ans: D

Incorrect Answers:

A. manual_scaling: instances: 5 min_pending_latency: 30ms

B. manual_scaling: max_instances: 5 idle_timeout: 10m

C. basic_scaling: instances: 5 min_pending_latency: 30ms

These other options are incorrect because manual_scaling doesn't allow you to set a maximum number of instances (it's a fixed number), and option C is using incorrect syntax for basic_scaling.



Correct Answer:

D. basic_scaling: max_instances: 5 idle_timeout: 10m

When you want to limit the number of instances in App Engine, you can use basic scaling with a specific maximum number of instances.

The correct code snippet for this configuration is:

basic_scaling: max_instances: 5 idle_timeout: 10m

This configuration ensures that App Engine will keep a maximum of 5 instances running and automatically shut down instances that have been idle for more than 10 minutes.



Links:

https://cloud.google.com/appengine/docs/legacy/standard/python/how-instances-are-managed#scaling_types

