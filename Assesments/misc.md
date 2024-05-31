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


### 2. How to build a container without using docker file?

Google Cloud supports buildpacks—an open-source technology that facilitates the rapid and effortless creation of secure, production-ready container images from source code, without needing a Dockerfile. https://cloud.google.com/blog/products/containers-kubernetes/google-cloud-now-supports-buildpacks

### 3. Deploy the application in Cloud Run from source code?

Deploying from source code is possible in Cloud Run. You can deploy new services and new revisions directly from source code using a single gcloud CLI command, gcloud run deploy, with the --source flag.

https://cloud.google.com/run/docs/deploying-source-code

### 4. You are writing a single-page web application with a user-interface that communicates with a third-party API for content using XMLHttpRequest. The data displayed on the UI by the API results is less critical than other data displayed on the same web page, so it is acceptable for some requests to not have the API data displayed in the UI. However, calls made to the API should not delay rendering of other parts of the user interface. You want your application to perform well when the API response is an error or a timeout.
What should you do?

- A. Set the asynchronous option for your requests to the API to false and omit the widget displaying the API results when a timeout or error is encountered.

- B. Set the asynchronous option for your request to the API to true and omit the widget displaying the API results when a timeout or error is encountered.

- C. Catch timeout or error exceptions from the API call and keep trying with exponential backoff until the API response is successful.

- D. Catch timeout or error exceptions from the API call and display the error response in the UI widget.

### Ans: B

Incorrect Answers:

A. Set the asynchronous option for your requests to the API to false and omit the widget displaying the API results when a timeout or error is encountered.

This would cause the requests to be handled synchronously, blocking other parts of the UI from rendering until the request is completed, which is the opposite of what is wanted.

C. Catch timeout or error exceptions from the API call and keep trying with exponential backoff until the API response is successful.

This would cause unnecessary delays and potentially keep trying indefinitely if the API continues to fail. Since the data is less critical, repeatedly trying to fetch it doesn't align with the requirements.

D. Catch timeout or error exceptions from the API call and display the error response in the UI widget.

Displaying error responses in the UI might be undesirable, especially if the data is less critical. Also, this doesn't address the requirement to make the call asynchronous.



Correct Answer:

B. Set the asynchronous option for your request to the API to true and omit the widget displaying the API results when a timeout or error is encountered.

In this scenario, the focus is on ensuring that calls to the third-party API don't delay rendering other parts of the UI, and it's acceptable if some requests to the API don't result in data being displayed.

So the best choice here is to make the request asynchronous (option B) so that it won't block other parts of the UI from rendering, and simply omit the widget if there's an error or timeout, as the data is less critical.

https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest


