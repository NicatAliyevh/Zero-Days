## SQL Injection Vulnerability (CWE-89)
## CVE-2025-63504

## Summary
A critical SQL Injection (SQLi) vulnerability exists within the admin-panel.php script. The application fails to properly sanitize or parameterize user-supplied input from the "docFees" parameter before incorporating it directly into a dynamic SQL query.
This flaw allows any authenticated user to execute arbitrary database commands, leading to severe impacts, including full Data Exposure, Data Corruption, and potential Server-Side Code Execution (via advanced database techniques).

## Vulnerable Component and Context
File: admin-panel.php
Access: Any Authenticated User
Vulnerable code:

$docFees=$_POST['docFees'];
Later in the code:
$query=mysqli_query($con,"insert into appointmenttb(pid,fname,lname,gender,email,contact,doctor,docFees,appdate,apptime,userStatus,doctorStatus) values($pid,'$fname','$lname','$gender','$email','$contact','$doctor','$docFees','$appdate','$apptime','1','1')");

## Proof of Concept (PoC)
The vulnerability is triggered by manipulating the docFees parameter. Since the input is not escaped or type-casted, an attacker can append SQL control characters to break out of the string context.
