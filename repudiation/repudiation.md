# Repudiation

The example demonstrates a vulnerability that can lead to repudiation by malicious users attempting to access the services provided by a server.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Run the server __insecure.ts__.

3. Pretend to be a malicous user and interact with the services by sending requests from the browser.

4. Do you think your actions can be repudiated?

## For you to do

1. Briefly explain the vulnerability.

It is not logging the request and response. If something goes wrong, we do not have this metadata to detect what happened and hold the entities involved accountable.

2. Briefly explain why the vulnerability is addressed in __secure.ts__.

It is addressed in **secure.ts** because it has middleware applicable to all routes and it logs information like the current date/time, type of request, IP address of requests and writes it into a log stream.

3. Which design pattern is used in the secure version to address the vulnerability? Briefly explain how it works?

In the secure non-repudiation version of this code, all actions are accounted for with thorough logging using the logStream **server.log**. This allows for the system to trace any malicious actions to the user and hold them accountable.