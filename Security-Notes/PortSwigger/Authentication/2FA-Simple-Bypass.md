## LAB: 2FA Simple Bypass

**Vulnerability:** 2FA Bypass - app considers user authenticated before 2FA code is verified

**Steps:**
- Sign in as target user (credentials known, no access to their 2FA code)
- After submitting credentials, manually navigate to `/my-account` before entering 2FA code
- If the app grants access, the 2FA step is not enforced server-side

**Bug Bounty Testing:** After submitting valid credentials but before
completing 2FA, try directly navigating to authenticated URLs, the
session may already be valid server-side
