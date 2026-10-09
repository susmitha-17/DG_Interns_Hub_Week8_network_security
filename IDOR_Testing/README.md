# IDOR Testing – OWASP Juice Shop

## Overview

This folder documents the Insecure Direct Object Reference (IDOR) and Broken Access Control testing performed during the Week 8 Advanced VAPT assessment. The assessment was conducted against OWASP Juice Shop running in an authorized local lab environment using Kali Linux, Ubuntu, and Burp Suite Community Edition.

## Objective

The objective was to evaluate whether an authenticated user could access another user's basket data by modifying an object identifier in an API request. This test focused on identifying weaknesses in server-side authorization and verifying whether the application enforced ownership checks for requested resources.

## Testing Methodology

1. Observed the authenticated user's basket request using Burp Suite.
2. Identified the request `GET /rest/basket/6`.
3. Modified the basket identifier from `6` to `1` using Burp Suite Repeater.
4. Sent the modified request to the local Juice Shop application.
5. Examined the HTTP response and returned JSON data.
6. Compared the basket owner identifier with the authenticated user's ID.

## Observed Result

The authenticated user was identified as User ID 25. After changing the request to `GET /rest/basket/1`, the application returned `HTTP/1.1 200 OK`. The response contained basket ID 1, UserId 1, and associated product information.

This demonstrated that User ID 25 could retrieve basket data belonging to User ID 1, confirming an IDOR/Broken Access Control issue involving unauthorized read access to another user's basket.

## Security Impact

The vulnerability may allow authenticated users to access other users' basket information by changing the basket identifier. This represents a failure of object-level authorization and may create privacy risks. The assessment confirmed access to basket and product information only; access to passwords, payment information, or other sensitive records was not demonstrated.

## Recommended Remediation

* Enforce server-side object-level authorization on every basket request.
* Verify that the requested basket belongs to the currently authenticated user.
* Never rely on a user-controlled identifier as proof of authorization.
* Reject unauthorized access with an appropriate response, such as HTTP 403 Forbidden.
* Apply consistent authorization checks across all relevant API endpoints.
* Add automated tests to verify that users cannot access other users' resources.

## Evidence

The screenshot `Task4_IDOR_Other_User_Basket.png` records the modified request and successful response in Burp Suite Repeater.

## Conclusion

The test confirmed an IDOR/Broken Access Control vulnerability in the local OWASP Juice Shop lab. It demonstrated the importance of implementing server-side ownership validation in addition to authentication. Testing was limited to the authorized local environment.
