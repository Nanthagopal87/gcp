### 1. You have an application that uses an HTTP Cloud Function to process user activity from both desktop browser and mobile application clients. This function will serve as the endpoint for all metric submissions using HTTP POST.
Due to legacy restrictions, the function must be mapped to a domain that is separate from the domain requested by users on web or mobile sessions. The domain for the Cloud Function is https://fn.example.com. Desktop and mobile clients use the domain https://www.example.com. You need to add a header to the function's
HTTP response so that only those browser and mobile sessions can submit metrics to the Cloud Function.

Which response header should you add?

- A. Access-Control-Allow-Origin: *

- B. Access-Control-Allow-Origin: https://*.example.com

- C. Access-Control-Allow-Origin: https://fn.example.com

- D. Access-Control-Allow-Origin: https://www.example.com

### Ans: D

Incorrect Answers:

A. Access-Control-Allow-Origin: *

Option A (*) would allow any domain to access the resource, which would not restrict access to the specific domain needed.

B. Access-Control-Allow-Origin: https://*.example.com

Option B (https://*.example.com) is not a valid value for the Access-Control-Allow-Origin header, as wildcards are not supported in this context except for the single * character.

C. Access-Control-Allow-Origin: https://fn.example.com

Option C (https://fn.example.com) would only allow access from the Cloud Function's own domain, which doesn't align with the requirement to allow access from the desktop and mobile client's domain.



Correct Answer:

D. Access-Control-Allow-Origin: https://www.example.com

This option explicitly allows only the specified domain (https://www.example.com) to access the resource, which meets the requirement stated.

Links:

https://cloud.google.com/functions/docs/samples/functions-http-cors

### 2. 