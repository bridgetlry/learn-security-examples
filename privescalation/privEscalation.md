# Privilege Escalation

The example demonstrates a privilege escalation vulnerability and how to exploit it.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Start the **insecure.ts** server

    `$ npx ts-node insecure.ts`

3. In the browser, send a GET request

    ```
        http://localhost:3000/send-form
    ```

4. Try different UserIds and see which one gives you authorized access to change the role of that user.

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**

The main issue is that there is weak authorization regarding logins and role assignments.

2. Briefly explain how a malicious attacker can exploit them.

A malicious hacker can send requests that change the roles, so they could set themselves as an admin.

3. Briefly explain the defensive techniques used in **secure.ts** to prevent the privilege escalation vulnerability?

In **secure.ts**, it has the server generate a session-id which it relies on instead of the roles potentially controlled by the hacker.