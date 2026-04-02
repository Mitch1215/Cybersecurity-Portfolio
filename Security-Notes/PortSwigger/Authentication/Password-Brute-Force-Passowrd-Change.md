## LAB: Password Brute-Force via Password Change

**Vulnerability:** Broken Authentication - different error messages on password change reveal correct current password

**Steps:**
- On password change page enter correct current password + two different new passwords
→ returns `New passwords do not match`
- Enter incorrect current password + two different new passwords
→ returns `Current password is incorrect`
- Send POST to Intruder, change username parameter to target user
- Set payload on current password field, add Grep Match for `New passwords do not match`
- The password that triggers that response is the target's valid current password

**Bug Bounty Testing:** Password change forms often have weaker
protections than login pages, different error messages based on
current password validity can be used to brute force without triggering
login lockouts
