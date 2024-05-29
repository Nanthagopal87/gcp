### 1. Your team is developing an ecommerce platform for your company. Users will log in to the website and add items to their shopping cart. Users will be automatically logged out after 30 minutes of inactivity. When users log back in, their shopping cart should be saved.

How should you store users' session and shopping cart information while following Google-recommended best practices?

- A. Store the session information in Pub/Sub, and store the shopping cart information in Cloud SQL.

- B. Store the shopping cart information in a file on Cloud Storage where the filename is the SESSION ID.

- C. Store the session and shopping cart information in a MySQL database running on multiple Compute Engine instances.

- D. Store the session information in Memorystore for Redis or Memorystore for Memcached, and store the shopping cart information in Firestore.

### Ans: D

ncorrect Answers:

A. Store the session information in Pub/Sub, and store the shopping cart information in Cloud SQL.

Pub/Sub is designed for event streaming and messaging, not for managing session information. Storing session data in Pub/Sub would not be an efficient or conventional use of the service. Cloud SQL is a fully managed relational database service that could be used to store shopping cart information, but using Firestore as mentioned in option D is more suitable

B. Store the shopping cart information in a file on Cloud Storage where the filename is the SESSION ID.

Accessing a Cloud Storage bucket is slow and expensive for session information. This is not a Google Cloud best practice.

C. Store the session and shopping cart information in a MySQL database running on multiple Compute Engine instances.

While you can manage a MySQL database across Compute Engine instances, it would not provide the same scalability and low-latency access for session information as Memorystore. This is not a Google Cloud best practice.



Correct Answer:

D. Store the session information in Memorystore for Redis or Memorystore for Memcached, and store the shopping cart information in Firestore.

When storing session and shopping cart information for an ecommerce platform, it's important to consider scalability, reliability, and security. One solution that follows Google-recommended best practices would be to use Memorystore for Redis or Memorystore for Memcached to store session information, and Firestore to store shopping cart information.

Memorystore can store session information and easily handle a large number of concurrent connections, which is crucial for an ecommerce platform where users are frequently logged in and adding items to their shopping carts.

Firestore can easily handle large amounts of semi-structured data, such as the items in a shopping cart. Firestore is also a scalable and reliable solution, and it supports automatic scaling and replication.

By separating the session information and shopping cart information into different services, you can increase security and avoid any potential data breaches. Using different services also allows you to scale them independently.

Following this, answer D is best option



Links:

https://cloud.google.com/memorystore/docs/redis/redis-overview