# Spoofing

This example demonstrates spoofind through two ways -- Stealing cookies programmatically and cross site request forgery (CSRF).

## Steps to reproduce the vulnerability

1. Install dependencies

    `$ npx install`

2. Start the **insecure.ts** server

    `npx ts-node insecure.ts`

3. Start the malicious server **mal.ts**

    `npx ts-node mal.ts`

4. Open __http://localhost:8000__ in a browser, type a name and Submit.

5. Open the __Application__ tab in the Browser's inspect pane. Find the __Cookies__ under __Storage__. You should see a __connect.sid__ cookie being set.

6. Open the HTML file __mal-steal-cookie.html__ file in the same browser (different tab). Open inspect and view the console.

7. Click the link in the HTML file. Do you see the cookie being stolen in the console?

8. Open the HTML file __mal-csrf.html__ file in the same browser (different tab). What do you see if the user has not logged out of **insecure.ts**? What do you see if the user has logged out? 


## For you to answer

1. Briefly explain the spoofing vulnerability in **insecure.ts**.

The spoofing vulnerability in **insecure.ts** is the lack of security regarding the cookie and session data. The session ID is sent and logged to the console with each request.

2. Briefly explain different ways in which vulnerability can be exploited.

With the session ID vulnerable, it could be used to impersonate a user and hijack their session. Additionally, there is a risk of cross-site request forgery (CSRF) that would take advantage of user's trust of a site and submit malicious requests. 

3. Briefly explain why **secure.ts** does not have the spoofing vulnerability in **insecure.ts**.

The server in **secure.ts** does not have this vulnerability because the cookie-related parameters in the session are more secure and do not allow for requests with cookie information to different domains.