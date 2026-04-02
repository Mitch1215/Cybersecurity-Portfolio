## LAB: 2FA Broken Logic

**Vulnerability:** Broken 2FA - verify parameter not tied to authenticated session, allowing code generation for arbitrary users

**Steps:**
- Sign in as yourself, capture the 2FA verification request in Burp
- Note the `verify` parameter, send to Repeater and change it to target username
- This generates a 2FA token for that user
- Sign in again with your credentials, submit wrong 2FA code, send to Intruder
- Change `verify` to target username, brute force `mfa-code` parameter
- 4-digit code = max 10,000 attempts, viable to brute force

**Bug Bounty Testing:** Check if the 2FA verify parameter is
independently changeable, if the server generates codes based on that
parameter alone without validating session context, you can generate
and brute force codes for any user
