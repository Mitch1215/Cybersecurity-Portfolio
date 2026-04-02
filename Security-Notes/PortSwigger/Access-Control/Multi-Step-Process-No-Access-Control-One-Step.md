## LAB: Multi-Step Process with No Access Control on One Step

**Vuln:** Broken Access Control — confirmation step of multi-step flow has no auth check

**Steps:**
- As admin, upgrade a user and capture the confirmation POST request in Burp
- Note the `username`, `action`, and session cookie in the body
- Send to Repeater, swap session cookie for your non-admin cookie
- Change username to yours and resend, confirm privilege escalation

**Bug Bounty Testing:** Multi-step flows (wizards, confirmations,
checkouts) often only protect the first step, always test each step
independently with lower-privilege credentials
