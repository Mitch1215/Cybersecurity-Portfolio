## LAB: Basic SSRF Against Another Back-End System

**Vulnerability:** SSRF - internal network IP range reachable via stockApi parameter

**Steps:**
- Intercept stock check POST request and send to Intruder
- Replace `stockApi` value with `http://192.168.0.§1§:8080/admin`
- Brute force last octet 1–255 with step of 1
- Identify valid IP by 200 response code
- Send confirmed IP to delete target user

**Key payloads/paths:**
- `http://192.168.0.[1-255]:8080/admin`
- `http://192.168.0.X:8080/admin/delete?username=carlos`

**Bug Bounty Testing:** When internal IP scanning is in scope,
start with `192.168.0.X` and common ports like 8080 rate limit
your requests to avoid overwhelming the server
