## LAB: Referer-Based Access Control

**Vuln:** Broken Access Control — server trusts Referer header to verify admin origin

**Steps:**
- As admin, upgrade a user and capture the request in Burp — note `Referer: /admin`
- As non-admin, attempt direct navigation to `admin-roles?username=carlos&action=upgrade`, confirm Unauthorized
- In Repeater, paste non-admin session cookie but keep `Referer: /admin` header intact
- Change username to yours and resend, confirm escalation succeeded

**Key headers:**
- `Referer: https://site.com/admin`

**Bug Bounty Testing:** If privileged actions check the Referer header
instead of server-side session permissions, you can spoof it. Always
check what headers a privileged request sends and whether the server
trusts them blindly
