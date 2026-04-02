## LAB: Username Enumeration via Different Responses

**Vulnerability:** Broken Authentication - different error messages reveal valid usernames

**Steps:**
- Submit invalid username/password and capture request in Burp
- Send to Intruder, brute force username field and look for different response length
- Use confirmed username to brute force password, look for 302 status code

**Bug Bounty Testing:** Any login page that returns "incorrect password"
vs "incorrect username" separately is leaking valid usernames, always
check error message wording carefully
