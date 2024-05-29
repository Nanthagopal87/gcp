### 1. You are building a highly available and globally accessible application that will serve static content to users. You need to configure the storage and serving components. You want to minimize management overhead and latency while maximizing reliability for users.

What should you do?

- A.

1. Create a managed instance group. Replicate the static content across the virtual machines (VMs)

2. Create an external HTTP(S) load balancer.

3. Enable Cloud CDN, and send traffic to the managed instance group.

- B.

1. Create an unmanaged instance group. Replicate the static content across the VMs.

2. Create an external HTTP(S) load balancer

3. Enable Cloud CDN, and send traffic to the unmanaged instance group.

- C.

1. Create a Standard storage class, regional Cloud Storage bucket. Put the static content in the bucket

2. Reserve an external IP address, and create an external HTTP(S) load balancer

3. Enable Cloud CDN, and send traffic to your backend bucket

- D.

1. Create a Standard storage class, multi-regional Cloud Storage bucket. Put the static content in the bucket.

2. Reserve an external IP address, and create an external HTTP(S) load balancer.

3. Enable Cloud CDN, and send traffic to your backend bucket.

### Ans: D

Incorrect Answers:

Option A & Option B: Relying on instance groups (whether managed or unmanaged) requires more management overhead to replicate and maintain the static content across VMs. Also, scaling is not required in the question provided.

Option C: Using a regional bucket limits the data to two specific locations within a region, which doesn't ensure global accessibility and low latency for users all around the world.



Correct Answer:

Option D.

1. Create a Standard storage class, multi-regional Cloud Storage bucket. Put the static content in the bucket.
2. Reserve an external IP address, and create an external HTTP(S) load balancer.
3. Enable Cloud CDN, and send traffic to your backend bucket.

For serving static content globally with minimized latency and management overhead, the best solution is to leverage Google Cloud's globally distributed system, like a multi-regional Cloud Storage bucket, with Cloud CDN for caching. Here's why option D is the best choice:

A multi-regional bucket ensures that the content is stored redundantly across multiple regions, providing high availability and global access with low latency.

An external HTTP(S) load balancer automatically routes user requests to the nearest global location.

Cloud CDN leverages Google's highly distributed edge caching to minimize latency for end users.



Links:

https://cloud.google.com/storage/docs/hosting-static-website

https://cloud.google.com/load-balancing/docs/https