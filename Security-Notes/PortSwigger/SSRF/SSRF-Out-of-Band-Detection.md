## LAB: Blind SSRF with Out-of-Band Detection

**Vulnerability:** Blind SSRF - application makes outbound requests via Referer header, detectable via Burp Collaborator

**Steps:**
- Intercept product page request and send to Repeater
- Right-click Referer header and select Insert Collaborator Payload
- Send request and check Collaborator tab using Poll Now
- Confirm DNS and HTTP interactions show the server is making outbound requests

**Key payloads/paths:**
- Burp Collaborator generated subdomain in Referer header

**Note:** Requires Burp Pro. Blind SSRF without a way to escalate impact
is typically low severity useful for confirming the vulnerability
exists but focus energy on chaining it into something impactful

**Bug Bounty Testing:** Blind SSRF is common but low value on its
own the real prize is chaining it to reach internal metadata endpoints
or internal admin services to demonstrate real impact
