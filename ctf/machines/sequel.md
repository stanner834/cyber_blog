# Sequel

In this Box we are going to break into a machine running SQL server. SQL  is a relational database and stored user information in rows and columes. Usually, SQL data contains PII, PHI, or sensitive data that we can gather. Other databases can store user information such as passwords.&#x20;



To start, lets scan the machine for services.&#x20;

nmap -sV -sC 10.129.95.232

We see the MySQL service running on port 3306, this is for managing SQL databases.&#x20;

Make sure to install the SQL service so we can begin to communicate with the server.&#x20;

sudo apt update && sudo apt install mysql\*

It is normal best practice to try to login with default credentials

mysql -h 10.129.95.232 -u root --skip-ssl

Looks like we had some luck and were able to login with default credentials.&#x20;

Run show databases to see the available databases

<figure><img src="../../.gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure>

HTB looks interesting, type USE htb; to being writing commands to the database.&#x20;

We have now successfully changed and loaded the database, we can run a couple other commands to find information. Refer to this link for help with SQL commands. [https://www.mysqltutorial.org/mysql-cheat-sheet/](https://www.mysqltutorial.org/mysql-cheat-sheet/)

SHOW tables;

<figure><img src="../../.gitbook/assets/image (118).png" alt=""><figcaption></figcaption></figure>

SELECT \* FROM config;

<figure><img src="../../.gitbook/assets/image (119).png" alt=""><figcaption></figcaption></figure>
