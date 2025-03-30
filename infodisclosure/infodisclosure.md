# Tampering

This example demonstrates information disclosure by injecting malicious query objects to a NoSQL database.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Insert test data in the MongoDB database. Make sure the mongod is up and running by typing the `mongosh` command in the termainal. If mongod process is up then you will see that the connection was successful. Command to insert test data:

    `$ npx ts-node insert-test-users.ts`

This will create a database in MongoDB called __infodisclosure__. Verify its presence by connecting with mongosh and running the command `show dbs;`.

2. Start the **insecure.ts** server

    `$ npx ts-node insecure.ts`

3. In the browser, pretend to be a hacker and type a malicious request

    ```
        http://localhost:3000/userinfo?username[$ne]=
    ```

4. Do you see user information being displayed despite the malicious request not having a valid username in the request?

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**

Running **insert-test-users.ts** prints out sensitive information (username, password, id). The username is being passed (unsanitized) to the query.

2. Briefly explain how a malicious attacker can exploit them.

A malicious attacker could pass mongoose queries in the url like **username[$ne]=** to find all usernames with a NoSQL injection attack. This is sensitive data that should not be this easily accessed.

3. Briefly explain the defensive techniques used in **secure.ts** to prevent the information disclosure vulnerability?

In **secure.ts**, we sanitize the username using a regular expression to replace any non alphanumeric characters.
