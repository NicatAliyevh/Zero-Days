## SQL Injection Vulnerability (CWE-89)
## CVE-2025-63515

## Summary
A critical SQL Injection (SQLi) vulnerability exists within the admin-panel.php script, specifically in the appointment cancellation logic. The application fails to properly sanitize or parameterize user-supplied input from the ID URL parameter before incorporating it directly into a dynamic SQL query.
This flaw allows any authenticated user to execute arbitrary database commands, leading to severe impacts, including full Data Exposure, Data Corruption, and potential Server-Side Code Execution (via advanced database techniques).

## Vulnerable Component and Context
File: admin-panel.php
Access: Any Authenticated User
Vulnerable code:
if(isset($_GET['cancel']))
{
$query=mysqli_query($con,"update appointmenttb set userStatus='0' where ID = '".$_GET['ID']."'");
if($query)
{
echo "<script>alert('Your appointment successfully cancelled');</script>";
}
}

## Proof of Concept (PoC)
The vulnerability is triggered by manipulating the ID parameter in the URL. Since the input is not escaped or type-casted, an attacker can append SQL control characters to break out of the string context.

## Malicious Payload
' or sleep(1) #

## Impact
1. Server-Side Code Execution, Data Exposure
