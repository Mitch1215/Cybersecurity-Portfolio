## LAB: Username Enumeration via Subtly Different Responses

**Vulnerability:** Broken Authentication - minor whitespace/punctuation difference in error reveals valid username

**Steps:**
- Submit invalid credentials and capture in Burp Intruder
- In Intruder settings use Grep Extract on the error message text
- Run username brute force and look for a subtly different response
(e.g. trailing `<p>` tag or extra space), that's the valid username
- Brute force password normally after

**Bug Bounty Testing:** When error messages look identical, check
response length and use Grep Extract in Intruder, differences are
sometimes invisible to the eye but show up in the data
