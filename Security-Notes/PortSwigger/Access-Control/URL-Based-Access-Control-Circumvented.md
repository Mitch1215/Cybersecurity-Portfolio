## LAB: URL-Based Access Control Can Be Circumvented

**Vuln:** Broken Access Control — backend trusts X-Original-URL header

**Steps:**
- Navigate to `/admin`, confirm Access Denied
- In Burp add `X-Original-URL: /invalid` header and change URL to `/`
- Confirm "not found" response (proves header is being processed)
- Change `X-Original-URL` value to `/admin` to access the panel

**Key headers:**
- `X-Original-URL: /admin`
- `X-Rewrite-URL` (alternate header to try)

**Bug Bounty Testing:** Use Wappalyzer to check backend framework,
then test X-Original-URL and X-Rewrite-URL headers on any Access Denied
or Forbidden endpoints
