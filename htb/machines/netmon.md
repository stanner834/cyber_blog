# Netmon

Let's start with a standard ping and nmap scan.

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

We see an FTP server is running on the machine, we can try to login using default credentials because the nmap script let us know that anonymous logins are allowed.&#x20;

anonymous:anonymous

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

You will find the user flag in /Users/Public/Desktop/flag.txt



Use the get command to download the file to you local machine.



Knowing that we are running a network monitor application, we can use the ftp access to see if we can see any interesting information from PRTG.&#x20;
