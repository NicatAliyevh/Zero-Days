## Privilege Escalation in Grav Admin: Missing Username Uniqueness Check Allows Admin Account Takeover
## CVE-2025-66296

## Summary
A privilege escalation vulnerability exists in Grav’s Admin plugin due to the absence of username uniqueness validation when creating users.
A user with the create user permission can create a new account using the same username as an existing administrator account, set a new password/email, and then log in as that administrator. This effectively allows privilege escalation from limited user-manager permissions to full administrator access.


## Steps to Reproduce
1. Make sure you have two accounts: an admin and a user with create user privilege
2. In the user account, navigate to /grav-admin/admin/accounts/users and click "Add"
3. Enter the name of the admin, complete registration and observe that the existing admin’s email is changed to the value you provided.
4. Log out from user account log in as admin with new credentials


## Impact
1. Full admin takeover by any user with create user permission.
2. Ability to change admin credentials, install/remove plugins, read or modify site data, and execute any action available to an admin.
3. Severity: High/Critical.


## Proof of Concept
https://github.com/user-attachments/assets/4ba7082a-51c6-4829-ac48-60fb07534478

