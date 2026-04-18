## LAB: SSRF with Filter Bypass via Open Redirection

**Vulnerability:** SSRF - open redirect in `/product/nextProduct?path=` used to reach internal services

**Steps:**
- Confirm direct host substitution in `stockApi` is blocked
- Find open redirect functionality (e.g. next product button) and intercept in Burp
- Note the `path` parameter in `/product/nextProduct?path=`
- Replace `stockApi` value with `/product/nextProduct?path=http://192.168.0.12:8080/admin`
- Confirm admin panel loads, then append delete path to execute action

**Key payloads/paths:**
- `/product/nextProduct?path=http://192.168.0.12:8080/admin`
- `/product/nextProduct?path=http://192.168.0.12:8080/admin/delete?username=carlos`

**Bug Bounty Testing:** When direct SSRF is blocked look for open
redirect functionality on the same app redirect parameters like
`?path=`, `?url=`, `?next=` can be chained with SSRF to reach
internal services indirectly
