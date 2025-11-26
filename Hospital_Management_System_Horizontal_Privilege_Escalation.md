## Horizontal Privilege Escalation Vulnerability
## CVE-2025-63516

## Summary
Just login as a normal user, then change the url from admin-panel.php to admin-panel1.php, you will have admin access. After this, an attacker can do anything that the admin has access to.

## Vulnerable Component and Context
File: admin-panel1.php 
Access: Any Authenticated User 

## Proof of Concept (PoC)
The vulnerability is triggered by manipulating the URL. Since the input is not checked, an attacker can become an admin

## Impact
1. Horizontal Privilege Escalation
