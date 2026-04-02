## LAB: Broken Brute-Force Protection, Multiple Credentials per Request

**Vulnerability:** Broken Authentication - JSON body accepts array of passwords in single request

**Steps:**
- Capture login request and confirm it uses a JSON body
- Send to Repeater and replace the password value with an array of your wordlist
- Format: `["password1","password2","password3"]`
- Look for 302 response, then open response in browser to land on authenticated session

**Bug Bounty Testing:** Always check if login requests use JSON.
If so, test whether the app accepts an array of values, bypassing
per-request brute force limits entirely
