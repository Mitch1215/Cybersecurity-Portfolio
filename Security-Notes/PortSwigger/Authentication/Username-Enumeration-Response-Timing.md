## LAB: Username Enumeration via Response Timing

**Vulnerability:** Broken Authentication - server takes longer to hash passwords for valid usernames

**Steps:**
- Test if lockout exists after failed attempts
- In Repeater, test valid username + very long password vs invalid username
- Valid username will show significantly longer response time (server is hashing)
- Brute force usernames using Pitchfork with `X-Forwarded-For` header to spoof IP and avoid lockout
- Confirm valid username by longest response time, then brute force password same way
- Look for 302 status code on successful password

**Key headers:**
- `X-Forwarded-For: [incrementing IP]`

**Bug Bounty Testing:** Response timing differences on login pages
can reveal valid usernames even when error messages are identical,
always test with a long password string to amplify the timing gap
