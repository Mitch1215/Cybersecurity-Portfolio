## LAB: Broken Brute-Force Protection, IP Block

**Vulnerability:** Broken Authentication - lockout counter resets on successful login

**Steps:**
- Confirm lockout triggers after 3 failed attempts but resets on valid login
- In Intruder use Pitchfork attack with two payload lists
- Username list alternates between your known account and target account
- Password list alternates between your known password and wordlist guesses
- Set Resource Pool to 1 concurrent request to prevent counter triggering
- Look for 302 on target account password guess

**Bug Bounty Testing:** Always test if a successful login resets the
lockout counter, if it does, you can interleave valid logins to bypass
brute force protection indefinitely
