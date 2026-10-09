## Attack Surface Mapping – Week 8 Advanced VAPT

This folder contains the documentation and evidence collected during the attack surface mapping phase of the Week 8 Advanced Vulnerability Assessment and Penetration Testing (VAPT) assignment. The assessment was conducted against OWASP Juice Shop, an intentionally vulnerable web application hosted in a local lab environment using Docker on Ubuntu Linux and accessed from Kali Linux.

The primary objective of this phase was to understand the application's structure, identify its accessible functionality, observe HTTP requests and responses, and map the available application routes and API endpoints before conducting further security testing.

**Activities performed:**

* Explored the application's login and user registration functionality.
* Examined the product search and browsing features.
* Inspected basket/cart functionality and related application requests.
* Used Burp Suite's Target → Site map feature to observe discovered routes and endpoints.
* Reviewed HTTP traffic to understand how the browser communicates with the application server.
* Identified areas for further testing, including authentication, session handling, input validation, parameter manipulation, and object-level access control.
* Organized the collected evidence for use in the final assessment report.

**Tools and environment:**

* OWASP Juice Shop
* Burp Suite Community Edition
* Kali Linux
* Ubuntu Linux
* Docker
* VirtualBox
* Web browser

**Evidence:**

`Task1_Burp_Attack_Surface_Site_Map.png`

**Outcome:**

This phase established the initial understanding of the application's attack surface and helped guide subsequent testing activities. The mapped functionality and observed endpoints provided a starting point for investigating potential security weaknesses, including the confirmed IDOR/Broken Access Control issue documented in the Week 8 assessment.

All testing was performed within the local, authorized training environment.
