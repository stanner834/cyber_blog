# Appointment

Appointment is a machine running a SQL server. A common vulnerability that comes from running SQL server is SQL injection, as seen in the OWASP top 10 Web vulnerabilities. SQL injection is dangerous as it can allow an attacker to gain access to a backend database containing customer information like PII. Most web applications have a backend database that is called to pull user information for authentication and other purposes. In this demo, we will perform SQL injection on a machine running Apache Web server on port 80.



First we can perform recon by using the nmap tool with the -sC and -sV switch.

nmap -sC -sV {target\_ip}

Apache is a very common web server, we see it is running 2.4.38 on a Debian machine.

Navigating to the IP address we are faced with a login page.

<figure><img src="../../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

We could try to brute force the login page, but that will likely end up in us being detection by the security measures on the other side. The next sensible tactic would be to test the login form for some sort of SQL injection vulnerability.&#x20;

Here is an example of how PHP & SQL code work:

```
<?php
mysql_connect("localhost", "db_username", "db_password"); # Connection to the SQL
Database.
mysql_select_db("users"); # Database table where user information is stored.
$username=$_POST['username']; # User-specified username.
$password=$_POST['password']; #User-specified password.
$sql="SELECT * FROM users WHERE username='$username' AND password='$password'";
# Query for user/pass retrieval from the DB.
$result=mysql_query($sql);
# Performs query stored in $sql and stores it in $result.
$count=mysql_num_rows($result);
# Sets the $count variable to the number of rows stored in $result.
if ($count==1){
# Checks if there's at least 1 result, and if yes:
$_SESSION['username'] = $username; # Creates a session with the specified $username.
$_SESSION['password'] = $password; # Creates a session with the specified $password.
header("location:home.php"); # Redirect to homepage.
}
```

This code is vulnerable to SQL injection attack by modifying the $sql variable. Anything we type into the login page will be stored in these variables. Notice in the code there are no regular expressions or functions that prohibite us from typing anything we would like. Special characters allow us to modify queries and run malicious commands. This term is called "input validation".



If you review the SQL statement above we can use a single quote and # symbol to essentially erase the password variable from being used in the $sql variable.&#x20;



For example, if in the username field we type admin'# it will look like this i the code

SELECT \* FROM users WHERE username='admin'#'  AND password='a'

Anything after the # just essentially gets voided. Since we void the password variable, the search will only look and validate if there is a username with the one we specified in the field. So if there is an account called "admin" it will match.&#x20;



The single quote closes the string prematurely, allowing you to enter more commands.&#x20;

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

After selecting the login button, you will see the flag.&#x20;

<figure><img src="../../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>
