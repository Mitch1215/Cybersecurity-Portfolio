## LAB: Username Enumeration via Account Lock

**Vulnerability:** Broken Authentication - lockout only triggers on valid usernames, revealing them

**Steps:**
- In Intruder use Cluster Bomb attack
- Add payload position to username and a blank payload position at end of body
- Set blank position to Null Payloads, generate 5, this repeats each username 5 times
- Valid username will return a lockout error, all others return invalid credentials

**Note:** Requires Burp Pro or a Python script to send requests fast enough
to trigger the lockout response

**Bug Bounty Testing:** If a lockout message only appears for certain
usernames, that itself is the enumeration vulnerability, the app is
confirming the account exists
