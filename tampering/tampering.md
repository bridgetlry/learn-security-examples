# Tampering

This example demonstrates tampering through script injection.

## Steps to reproduce

1. Install all dependencies

    `npm install`

2. Start the **insecure.ts** server

    `npx ts-node insecure.ts`

3. In the browser, type a potentially malicious script in the name field of the form

    ```
        <script> document.body.innerHTML = "<a href='https://google.com'> Gotcha </a>"</script>
    ```

4. Do you see the potentially malicious hyperlink being injected into the form?

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**

The input is not sanitized in line 58, is directly using the users input without testing it for any executable or malicious code. It implicitly assumes that this input will be an alphanumeric string.

2. Briefly explain how a malicious attacker can exploit them.

A malicious attacker can execute a cross-site scripting attack and inject code and make server execute it, linked to go to a potentially malicious website.

3. Briefly explain why **secure.ts** does not have the same vulnerabilties?

**secure.ts** uses escapeHTML to sanitize the input to replace any special characters to their string version so it is no longer executable.
