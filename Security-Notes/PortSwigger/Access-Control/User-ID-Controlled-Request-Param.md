## LAB: User ID Controlled by Request Parameter

**Vulnerability:** Horizontal Broken Access Control - user ID exposed and trusted in URL

**Steps:**
- Note your username in the URL: `my-account?id=wiener`
- Change the value to another known username
- Confirm account switch and access to their data (e.g. API key)

**Key params:**
- `my-account?id=wiener` → `my-account?id=carlos`

**Bug Bounty Testing:** Look for any account identifier in the URL
and try substituting another known username or ID value
