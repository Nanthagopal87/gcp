### 1. You have two tables in an ANSI-SQL compliant database with identical columns that you need to quickly combine into a single table, removing duplicate rows from the result set.

What should you do?

- A. Use the JOIN operator in SQL to combine the tables.
- B. Use nested WITH statements to combine the tables.
- C. Use the UNION operator in SQL to combine the tables.
- D. Use the UNION ALL operator in SQL to combine the tables.

### ANS: C

### 2. You work for an organization that manages an online ecommerce website. Your company plans to expand across the world; however, the estore currently serves one specific region. You need to select a SQL database and configure a schema that will scale as your organization grows. You want to create a table that stores all customer transactions and ensure that the customer (CustomerId) and the transaction (TransactionId) are unique.

What should you do?

- A. Create a Cloud SQL table that has TransactionId and CustomerId configured as primary keys. Use an incremental number for the TransactionId.

- B. Create a Cloud SQL table that has TransactionId and CustomerId configured as primary keys. Use a random string (UUID) for the TransactionId.

- C. Create a Cloud Spanner table that has TransactionId and CustomerId configured as primary keys. Use a random string (UUID) for the TransactionId.

- D. Create a Cloud Spanner table that has TransactionId and CustomerId configured as primary keys. Use an incremental number for the TransactionId.

### Ans: C

This is the correct option, as it uses Cloud Spanner and also uses a UUID to avoid hotspot issues.

https://cloud.google.com/spanner/docs/schema-design#uuid_primary_key


