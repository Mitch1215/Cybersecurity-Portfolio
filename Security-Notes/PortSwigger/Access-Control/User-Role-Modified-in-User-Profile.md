## LAB: User Role Can Be Modified in User Profile

**Vuln:** Broken Access Control — role ID accepted in POST request body

**Steps:**
- Update your email and capture the POST request in Burp
- Check the response body for a `roleid` value
- Send request to Repeater, add `"roleid":2` to the request body
- Resend and confirm response shows updated role, then navigate to `/admin`

**Key params:**
- `roleid:1` (default) → `roleid:2` (admin)

**Bug Bounty Testing:** Always check response bodies after profile
updates for role or privilege identifiers, if they appear in the response,
try injecting them into the request
