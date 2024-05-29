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