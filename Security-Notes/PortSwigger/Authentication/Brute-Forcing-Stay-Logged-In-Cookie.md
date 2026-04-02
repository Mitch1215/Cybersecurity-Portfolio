## LAB: Brute-Forcing a Stay-Logged-In Cookie

**Vulnerability:** Broken Authentication - stay-logged-in cookie is a predictable hash of the user's password

**Steps:**
- Log in with stay-logged-in checked, capture cookie in Burp
- Decode and identify the structure (e.g. `base64(username:md5(password))`)
- Send request to Intruder, set payload on cookie value
- Under Payload Processing: Hash MD5 → add username prefix → encode Base64
- Look for response containing `Update email` to confirm valid cookie

**Bug Bounty Testing:** Always decode stay-logged-in cookies and
check if their contents are predictable, MD5 hashes of passwords are
commonly used and easily crackable
