### 1. Your existing application keeps user state information in a single MySQL database. This state information is very user-specific and depends heavily on how long a user has been using an application. The MySQL database is causing challenges to maintain and enhance the schema for various users.

Which storage option should you choose?

- A. Cloud SQL
- B. Cloud Storage
- C. Cloud Spanner
- D. Cloud Datastore/Firestore

### Ans: D 
NoSQL databases designed for web and mobile applications. They offer the flexibility of schemaless data, making them suitable for applications that require flexible schemas. Firestore, in particular, is the next version of Datastore and offers improved real-time capabilities and richer query capabilities.

Given the described scenario, the challenges lie in schema management and enhancement for various users. A NoSQL database, which inherently supports flexible schema design, might be the most suitable solution.

https://cloud.google.com/datastore/docs/concepts/overview#what_its_good_for
