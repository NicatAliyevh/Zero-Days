## Stored Cross-Site Scripting (XSS) 
## CVE-2025-63514

## Summary
A Cross-Site Scripting (XSS) vulnerability was identified in appsearch.php via the email parameter. Although the UI restricts email input, an attacker can bypass this restriction (e.g., using Burp Suite) and register with a malicious email like "<script>alert(1)</script>@gmail.com". When the user books an appointment, this input is stored and later rendered in the admin panel. Viewing available appointments causes the script to execute in the admin’s browser, posing a security risk.

## Vulnerable Component and Context
File: appsearch.php 
Access: Any Authenticated User 
Vulnerable code: 
echo "
$fname
$lname
$email
$contact
$doctor
$docFees
$appdate
$apptime
$appstatus
";

## Proof of Concept (PoC)
The vulnerability is triggered by manipulating the email parameter. Since the input is not escaped or type-casted, an attacker can append XSS control characters to break out of the string context.

## Malicious Payload
<script>alert(1)</script>@gmail.com

## Impact
1. Client-Side Code Execution
2. Privilege Escalation
