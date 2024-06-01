### 1. You have a Java application running on Cloud Run. Your application’s error messages do not appear in the Error Reporting console. What should you do?

- A. Ensure that Cloud Monitoring client libraries are bundled with the Java application.

- B. Verify that application logs are being written to the correct regional storage bucket.

- C. Verify that application errors are being written to stderr.

- D. Log exceptions using System.out.println.

### Ans: C

Incorrect Answers:

A. Ensure that Cloud Monitoring client libraries are bundled with the Java application.

Cloud Monitoring client libraries are not required for error reporting in Cloud Run, as the service handles the log collection process internally.

B. Verify that application logs are being written to the correct regional storage bucket.

Error Reporting does not analyze logs stored in regional log buckets, so verifying this would not address the problem.

D. Log exceptions using System.out.println.

Using System.out.println writes output to the standard output stream (stdout) rather than stderr, so it would not result in error messages appearing in the Error Reporting console.



Correct Answer:

C. Verify that application errors are being written to stderr.

In Cloud Run, error messages must be written to the standard error stream (stderr) for them to be recognized by Error Reporting. Ensuring that application errors are written to stderr would resolve the issue.

Links:

https://cloud.google.com/error-reporting/docs/troubleshooting

https://cloud.google.com/run/docs/error-reporting

### 2. 