## LAB: Unprotected Admin Functionality with Unpredictable URL

**Vuln:** Broken Access Control - admin panel URL hidden but exposed in client-side JavaScript

**Steps:**
- View page source (Ctrl+U or right-click → View Source)
- Search for keywords like `admin`, `panel`, `directory` in the JavaScript
- Navigate to any admin paths found

**Key paths/patterns:**
- Look for JS variables like `AdminPanelTag` pointing to a directory
- Paths may look randomized e.g. `/administrator-panel-wxyz` but are still accessible

**Bug Bounty Testing:** Always read page source early in recon,
developers sometimes hardcode sensitive URLs or API endpoints in
client-side JS thinking obscurity equals security
