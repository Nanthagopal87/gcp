### 1. You are parsing a log file that contains three columns: a timestamp, an account number (a string), and a transaction amount (a number). You want to calculate the sum of all transaction amounts for each unique account number efficiently.
Which data structure should you use?

- A. A linked list
- B. A hash table
- C. A two-dimensional array
- D. A comma-separated string

### Ans: B

Overall explanation
Incorrect Answers:

A. A linked list

A linked list would not provide efficient lookup or insertion of account numbers. You would need to traverse the list to find the correct account number every time, resulting in an inefficient O(n) time complexity for each search or insertion.

C. A two-dimensional array

A two-dimensional array would also require you to search through the array to find the correct account number every time you want to update a transaction amount, leading to inefficient O(n) time complexity.

D. A comma-separated string

A comma-delimited string is not a practical data structure for performing arithmetic calculations or efficient lookups. It would require parsing the string every time you want to update or find a value.



Correct Answer:

B. A hash table

A hash table is the correct choice for this scenario. You can use the account numbers as keys and the sums of the transaction amounts as values. This allows for efficient O(1) average time complexity for both search and insertion, making it easy to keep track of the transaction sums for each account number.

Links:

https://open4tech.com/array-vs-linked-list-vs-hash-table/



