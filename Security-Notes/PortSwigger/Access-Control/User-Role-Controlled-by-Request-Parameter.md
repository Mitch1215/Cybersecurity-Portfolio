## LAB: User Role Controlled by Request Parameter

**Vulnerability:** Broken Access Control — admin status controlled by client-side cookie parameter

**Steps:**
- Sign in and intercept navigation to `/admin` in Burp
- Look for `Admin=false` in the request parameters
- Change `Admin=false` to `Admin=true` to access the admin panel
- Repeat the intercept when deleting a user to maintain the modified value

**Key params/paths:**
- `my-account?id=wiener`
- `Admin=false` → `Admin=true`

**Bug Bounty Testing:** Look for any trust of client-supplied values
like admin status in cookies or parameters, if the server doesn't verify
server-side, you can just change it
