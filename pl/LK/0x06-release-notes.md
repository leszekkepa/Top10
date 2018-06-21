# RN Uwagi do wydania

## Co się zmieniło między wydaniami 2013 i 2017?

Wiele się zmieniło przez ostatnie cztery lata i OWASP Top 10 wymagał przeglądu. Zupełnie przeorganizowaliśmy OWASP Top 10, odświezyliśmy metodologię używając nowego procesu data call, współpracowaliśmy ze społecznością, zmieniliśmy kolejność ryzyk, przepisaliśmy gruntownie każde ryzyko oraz dodaliśmy odniesienia do popularnych frameworków i języków programowania.

Przez kilka ostatnich lat technologia i architektura aplikacji zmieniła się znacząco:

* Mikroserwisy (miniusługi?) written in node.js and Spring Boot are replacing traditional monolithic applications. Microservices come with their own security challenges including establishing trust between microservices, containers, secret management, etc. Old code never expected to be accessible from the Internet is now sitting behind an API or RESTful web service to be consumed by Single Page Applications (SPAs) and mobile applications. Architectural assumptions by the code, such as trusted callers, are no longer valid.
* Single page applications, written in JavaScript frameworks such as Angular and React, allow the creation of highly modular feature-rich front ends. Client-side functionality that has traditionally been delivered server-side brings its own security challenges.
* JavaScript jest obecnie primary language of the web with node.js running server side and modern web frameworks such as Bootstrap, Electron, Angular, and React running on the client.

## New issues, supported by data

* **A4:2017-XML External Entities (XXE)** is a new category primarily supported by source code analysis security testing tools ([SAST](https://www.owasp.org/index.php/Source_Code_Analysis_Tools)) data sets.

## New issues, supported by the community

We asked the community to provide insight into two forward looking weakness categories. After over 500 peer submissions, and removing issues that were already supported by data (such as Sensitive Data Exposure and XXE), the two new issues are: 

* **A8:2017-Insecure Deserialization**, which permits remote code execution or sensitive object manipulation on affected platforms.
* **A10:2017-Insufficient Logging and Monitoring**, the lack of which can prevent or significantly delay malicious activity and breach detection, incident response, and digital forensics.

## Merged or retired, but not forgotten

* **A4-Insecure Direct Object References** and **A7-Missing Function Level Access Control** merged into **A5:2017-Broken Access Control**.
* **A8-Cross-Site Request Forgery (CSRF)**, as many frameworks include [CSRF defenses](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)), it was found in only 5% of applications.
* **A10-Unvalidated Redirects and Forwards**, while found in approximately in 8% of applications, it was edged out overall by XXE.

![0x06-release-notes-1](images/0x06-release-notes-1.png)
