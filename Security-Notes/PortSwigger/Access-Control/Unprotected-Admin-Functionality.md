## LAB: Unprotected Admin Functionailty
**Vulnerability:** Broken Access Control - admin panel exposed via robots.txt

**Steps:**
- Navigate to `/robots.txt` and look for disallowed directories
- Manually browse to any sensitive paths listed
- Check what privileged actions are available without authentication

**Key payloads/paths:**
- `/robots.txt`
- `/administrator-panel`

**Bug bounty testing:** Always check robots.txt early in recon, disallowed paths often reveal admin panels or sensitive endpoints that aren't linked anywhere in the UI
