## SQL Injection Vulnerability (CWE-89)

## Summary
A critical SQL Injection (SQLi) vulnerability exists within the admin-panel1.php script, specifically in the deleting doctor logic. The application fails to properly sanitize or parameterize user-supplied input from the demail parameter before incorporating it directly into a dynamic SQL query. This flaw allows any authenticated user to execute arbitrary database commands, leading to severe impacts, including full Data Exposure, Data Corruption, and potential Server-Side Code Execution (via advanced database techniques).

## Vulnerable Component and Context
File: admin-panel1.php 
Access: Admin User 
Vulnerable code:
$demail=$_POST['demail']; ###this line uses demail parameter directly from the user input

if(isset($_POST['docsub1']))
{
$demail=$_POST['demail'];
$query="delete from doctb where email='$demail';";
$result=mysqli_query($con,$query);
if($result)
{
echo "<script>alert('Doctor removed successfully!');</script>";
}
else{
echo "<script>alert('Unable to delete!');</script>";
}

## Proof of Concept (PoC)
The vulnerability is triggered by manipulating the demail parameter. Since the input is not escaped or type-casted, an attacker can append SQL control characters to break out of the string context.

## Malicious Payload
' or sleep(1) #

## Impact
Server-Side Code Execution, Data Exposure


