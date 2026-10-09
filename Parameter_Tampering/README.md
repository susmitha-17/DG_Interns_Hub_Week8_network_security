### Parameter Tampering

This folder contains evidence and documentation of parameter tampering tests performed during the Week 8 Advanced Vulnerability Assessment and Penetration Testing (VAPT) assessment on OWASP Juice Shop in an authorized local lab environment.

Burp Suite Community Edition was used to intercept, inspect, modify, and replay HTTP requests to evaluate how the application validates user-controlled parameters and handles unexpected input.

The tests included modifying basket identifiers, changing registration security-question IDs, submitting invalid product IDs, and testing invalid basket quantities. Responses were analyzed to identify authorization weaknesses, input-validation problems, and improper error handling.

**Key observations:**

* Changing the BasketId in a basket-item creation request was rejected with an HTTP 401 Unauthorized response and an "Invalid BasketId" message.
* Changing the registration security-question ID resulted in an HTTP 400 Bad Request validation error.
* Submitting an invalid ProductId resulted in an HTTP 500 Internal Server Error and exposed an internal application stack-trace path.
* Testing zero and negative quantities also produced HTTP 500 errors, indicating a potential input-validation and error-handling weakness. A successful business-logic bypass was not demonstrated.

The findings emphasize the importance of server-side parameter validation, object-level authorization, controlled error responses, and avoiding exposure of internal implementation details.
