## IDOR Vulnerability

## Summary
An Insecure Direct Object Reference (IDOR) vulnerability was identified in the appointment cancellation functionality. The application allows users to cancel appointments by modifying the ID parameter in the GET request. This flaw enables an attacker to cancel any user's appointment without proper authorization.

## Vulnerable Component and Context
File: admin-panel.php 
Access: Any Authenticated User 
Vulnerable code: if(isset($_GET['cancel'])) { $query=mysqli_query($con,"update appointmenttb set userStatus='0' where ID = '".$_GET['ID']."'"); if($query) { echo "<script>alert('Your appointment successfully cancelled');</script>"; } }

## Proof of Concept (PoC)
The vulnerability is triggered by manipulating the ID parameter in the URL. Since the input is not checked, an attacker can cancel anyone's appointment

## Impact
1. Vertical Privilege Escalation

