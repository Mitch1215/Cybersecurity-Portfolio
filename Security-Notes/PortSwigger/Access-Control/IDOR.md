
## LAB: Insecure Direct Object References (IDOR)

**Vulnerability:** IDOR - sequential filenames in download requests allow access to other users' files

**Steps:**
- Use the live chat and download your transcript
- Note the filename (e.g. `2.txt`) in the request
- Send to Repeater and change filename to `1.txt` or other values
- Check responses for other users' chat data

**Key paths:**
- `/download-transcript/2.txt` → `/download-transcript/1.txt`

**Bug Bounty Testing:** Any file download functionality with a
predictable filename or ID in the request is worth testing, increment
or decrement the value and check the response
