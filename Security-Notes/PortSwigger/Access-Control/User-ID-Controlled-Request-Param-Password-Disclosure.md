## LAB: User ID Controlled by Request Parameter with Password Disclosure

**Vuln:** Horizontal to Vertical Privilege Escalation — password visible in response, ID swappable in URL

**Steps:**
- Sign in and navigate to your account, note `id=` value in URL
- Change ID to `administrator` in the URL
- Trigger a password update, observe admin password in the request/response
- Sign in as admin and delete target user

**Bug Bounty Testing:** When you can switch user context via URL and
the app exposes password fields in responses, you can chain horizontal
into vertical escalation
