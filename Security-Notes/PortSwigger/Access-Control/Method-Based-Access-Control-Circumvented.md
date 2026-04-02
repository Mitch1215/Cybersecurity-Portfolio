## LAB: Method-Based Access Control Can Be Circumvented

**Vuln:** Broken Access Control - server only restricts POST, not GET for privileged actions

**Steps:**
- As admin, capture the privilege upgrade request and note the parameters
- Switch to non-admin session cookie in Repeater — confirm Unauthorized
- Change `POST` to `POSTX`, confirm "missing parameter" (proves method checking is weak)
- Convert to `GET` request with your username and `action=upgrade`

**Key params/paths:**
- `admin-roles?username=user&action=upgrade`

**Note:** Horizontal privilege escalation = accessing another user's resources.
Vertical = gaining higher privilege than your own account has.

**Bug Bountry Testing:** When you find privileged actions, always test
alternate HTTP methods (GET, PUT, POSTX), access controls are often only
applied to the expected method
