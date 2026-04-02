## LAB: 2FA Bypass Using a Brute-Force Attack

**Vulnerability:** Broken 2FA - code can be brute forced using Burp macro to re-authenticate after each logout

**Steps:**
- Confirm the app logs you out after 2 failed 2FA attempts
- In Burp Session Handling Rules, set scope to Include All URLs
- Create a macro: `GET /login` → `POST /login` → `GET /login2`
- Test macro and confirm final response contains the 2FA code entry page
- Send `POST /login2` to Intruder, set payload on `mfa-code`
- Use Numbers payload type, range 0–9999
- Set Resource Pool to 1 concurrent request
- Look for 302 status code

**Remember for bug bounty:** If 2FA codes are short and numeric, brute
forcing is viable, use Burp macros to handle re-authentication
automatically when the app forces logout on failed attempts
