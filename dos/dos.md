# Denial-of-Service (DoS)

This example demonstrates DoS vulnerabilities and how they can be exploited.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Ignore if you have already done this once. Insert test data in the MongoDB database. Make sure the mongod is up and running by typing the `mongosh` command in the termainal. If mongod process is up then you will see that the connection was successful. Command to insert test data:

    `$ npx ts-node insert-test-users.ts`

This will create a database in MongoDB called __infodisclosure__. Verify its presence by connecting with mongosh and running the command `show dbs;`.

2. Start the **insecure.ts** server

    `$ npx ts-node insecure.ts`

3. In the browser, pretend to be a hacker and type a malicious request

    ```
        http://localhost:3000/userinfo?id[$ne]=
    ```

4. Do you see the server crashing?

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts** that can lead to a DoS attack.

There is no functionality to handle when the system crashes or when the site is flooded with requests.

2. Briefly explain how a malicious attacker can exploit them.

A malicious hacker could repeatedly send more requests than the server can handle and render the system unusable.

3. Briefly explain the defensive techniques used in **secure.ts** to prevent the DoS vulnerability?

In addition to sanitizing the input like with the other attacks, **secure.ts** uses try-catch statements to handle the error. It also has a rate limit middleware applied to applicable routes, only allowing a certain number of requests in a given time frame. The server doesn’t crash but rather it presents descriptive errors to indicate what the issue is.