## LAB: Basic SSRF Against the Local Server

**Vulnerability:** SSRF - stockApi parameter accepts arbitrary URLs, allowing requests to localhost

**Steps:**
- Confirm `/admin` is blocked when accessed directly
- Use stock check feature and intercept POST request in Burp
- Replace `stockApi` value with `http://localhost/admin` to load admin panel
- Capture the delete user request URL from the admin panel
- Replace `stockApi` value with delete URL to execute the action

**Key payloads/paths:**
- `http://localhost/admin`
- `http://127.0.0.1/admin`
- `http://localhost/admin/delete?username=carlos`

**Bug Bounty Testing:** Look for any POST request that contains a
URL parameter hitting a back-end API stock checkers, webhook fields,
PDF generators, and image fetchers are common places to find this.
Always try `localhost` and `127.0.0.1` first
