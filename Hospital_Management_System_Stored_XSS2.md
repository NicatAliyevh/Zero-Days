## Stored Cross-Site Scripting (XSS) 
## CVE-2025-63507

## Summary
Hospital Management System v4 was discovered to contain multiple cross-site scripting (XSS) vulnerabilities in admin-panel1.php via the username, spec, email, password, and docFees parameters.

## Vulnerable Component and Context
File: adminpanel1.php
Access: Any Authenticated User
  echo "<tr>
    <td>$username</td>
    <td>$spec</td>
    <td>$email</td>
    <td>$password</td>
    <td>$docFees</td>
  </tr>";
  These parameters are not sanitized when a user registers, and here they are used without any filter

## Impact
1. Client-Side Code Execution
2. Privilege Escalation
