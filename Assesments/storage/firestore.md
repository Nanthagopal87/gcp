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


### 2. You are designing a chat room application that will host multiple rooms and retain the message history for each room. You have selected Firestore as your database.

How should you represent the data in Firestore?

- A. Create a collection for the rooms. For each room, create a document that lists the contents of the messages.

- B. Create a collection for the rooms. For each room, create a collection that contains a document for each message.

- C. Create a collection for the rooms. For each room, create a document that contains a collection for documents, each of which contains a message.

- D. Create a collection for the rooms, and create a document for each room. Create a separate collection for messages, with one document per message. Each room’s document contains a list of references to the messages.

Incorrect Answers:

A. Create a collection for the rooms. For each room, create a document that lists the contents of the messages.

This approach would not scale well if you have a large number of messages in each room, as you would be trying to keep all messages within a single document.

B. Create a collection for the rooms. For each room, create a collection that contains a document for each message.

A collection for the rooms, each having a subcollection of messages, creates a many-to-many relationship, which is not suitable for Firestore.

D. Create a collection for the rooms, and create a document for each room. Create a separate collection for messages, with one document per message. Each room’s document contains a list of references to the messages.

This approach separates rooms and messages into different collections but then requires maintaining references between them, which could be more complex to handle and query.



Correct Answer:

C. Create a collection for the rooms. For each room, create a document that contains a collection for documents, each of which contains a message.

The best approach to store messages in this scenario is by using subcollections. A subcollection is a collection associated with a specific document.



Links:

https://firebase.google.com/docs/firestore/data-model#hierarchical-data

https://firebase.google.com/docs/firestore/data-model#subcollections


### 3. You are a lead developer working on a new retail system that runs on Cloud Run and Firestore in Datastore mode. A web UI requirement is for the system to display a list of available products when users access the system and for the user to be able to browse through all products. You have implemented this requirement in the minimum viable product (MVP) phase by returning a list of all available products stored in Firestore.



A few months after go-live, you notice that Cloud Run instances are terminated with HTTP 500: Container instances are exceeding memory limits errors during busy times. This error coincides with spikes in the number of Datastore entity reads. You need to prevent Cloud Run from crashing and decrease the number of Datastore entity reads. You want to use a solution that optimizes system performance.

What should you do?

- A. Modify the query that returns the product list using integer offsets.

- B. Modify the query that returns the product list using limits.

- C. Modify the Cloud Run configuration to increase the memory limits.

- D. Modify the query that returns the product list using cursors.

### Ans: D

Incorrect Answers:

A. Modify the query that returns the product list using integer offsets.

Although Datastore mode databases support integer offsets, you should avoid using them and use cursors instead. Using an offset only avoids returning the skipped entities to application, but these entities are still retrieved internally. These skipped entities do affect the latency of the query, and your application is billed for the read operations required to retrieve them. By using cursors instead of offsets, you can avoid all these costs.

B. Modify the query that returns the product list using limits.

Using limits in a query restricts the number of results returned in a single response, but it does not manage the state between multiple requests. So, if you have many products and want to allow users to browse through them all, merely limiting the results doesn't provide a way to efficiently paginate through the entire list. Each new request would start from the beginning, and you would have no efficient way to continue from where the last request left off.

C. Modify the Cloud Run configuration to increase the memory limits.

While increasing the memory limits of Cloud Run instances could help alleviate the issue temporarily, it would not address the root cause of the problem, which is the high number of Datastore entity reads during busy times. Over time, as more products are added to the system, this problem would only become more severe, and you would have to continually increase the memory limits to prevent Cloud Run from crashing



Correct Answer:

D. Modify the query that returns the product list using cursors.

Using cursors to paginate the results and retrieve a limited number of products at a time offers a more sustainable solution. It reduces the amount of data that needs to be read from Datastore and decreases the memory usage of your Cloud Run instances. This way, you can maintain the performance of the system and prevent it from crashing, even as more products are added over time.



Links:

https://cloud.google.com/datastore/docs/concepts/queries#cursors


### 4. You are a developer at a social media company. The company currently runs its social media website on-premises and uses MySQL as a backend to store user profiles and user posts. Your company plans to migrate to Google Cloud, and your team will migrate user profile information to Firestore. Your task is to design the Firestore collections.

What should you do?

- A. Create one root collection for user profiles and one root collection for user posts.

- B. Create one root collection for user profiles and create one subcollection for each user's posts.

- C. Create one root collection for user profiles and store each user's posts as a nested list in the user profile document.

- D. Create one root collection for user posts and create one subcollection for each user's profile.

### Ans: A

Incorrect Answers:

B. Create one root collection for user profiles and create one subcollection for each user's posts.

In this option, each user profile document in the root collection has a subcollection for that user's posts. This design maintains a clear hierarchical relationship between profiles and posts and supports efficient querying within a user's posts. It is also scalable, as Firestore handles large numbers of subcollections well. However, querying across all posts from all users is more complex and less efficient compared to having a separate root collection for posts.

C. Create one root collection for user profiles and store each user's posts as a nested list in the user profile document.

This option involves storing posts directly within the user profile document as an array or list. While this design simplifies the data model by consolidating user data in a single document, it has limitations in scalability and query performance. Firestore documents have a size limit (currently 1 MiB), and large numbers of posts could exceed this limit. Additionally, querying and updating individual posts within a nested list can be cumbersome and less efficient.

D. Create one root collection for user posts and create one subcollection for each user's profile.

This design is less practical for a social media application, as it reverses the typical relationship between posts and profiles. User profiles are usually the primary entity, with posts being related to them. This approach would make common queries, like retrieving a user's profile and their posts, less intuitive and efficient.

Correct answer:

A. Create one root collection for user profiles and one root collection for user posts.

This approach involves two separate root collections: one for user profiles and another for user posts. It supports scalability and efficient querying, as each collection can be queried independently. This design is suitable for large datasets and allows for flexible queries on both profiles and posts.

Option A (creating one root collection for user profiles and one root collection for user posts) is the most suitable for a social media website. It offers a scalable and efficient structure for handling large numbers of user profiles and posts, allows for flexible and efficient querying, and maintains a clear separation of concerns between user profiles and posts. While it requires managing the relationship between profiles and posts, this can be efficiently handled with proper indexing and query design.

### 5. Your company needs a database solution that stores customer purchase history and meets the following requirements:

Customers can query their purchase immediately after submission.

Purchases can be sorted based on a variety of fields.

Distinct record formats can be stored simultaneously.

Which storage option satisfies these requirements?

- A. Firestore in Native mode

- B. Cloud Storage using object reading

- C. Cloud SQL using a SQL SELECT statement

- D. Firestore in Datastore mode using a global query

### Ans: A

Incorrect Answers:

B. Cloud Storage using object reading

Cloud Storage is an object storage service, which doesn't offer immediate querying or sorting based on fields. It's suitable for storing unstructured data but doesn't provide database-like querying capabilities.

C. Cloud SQL using a SQL SELECT statement

While Cloud SQL (a relational database service) does allow querying and sorting, it doesn't natively handle distinct record formats as NoSQL databases do. Schema changes would be required to accommodate different formats, making it less suitable for the described use case.

D. Firestore in Datastore mode using a global query

Datastore mode in Firestore is also a NoSQL database service that might seem suitable. However, the Native mode of Firestore has more robust indexing and querying capabilities, making it a better fit for the requirements.



Correct Answer:

A. Firestore in Native mode

Firestore in Native mode offers flexible and scalable NoSQL database storage. It allows clients to read their writes immediately and provides indexing and sorting capabilities on various fields. The distinct record formats can be stored as documents with different fields.

Links:

https://cloud.google.com/datastore/docs/firestore-or-datastore