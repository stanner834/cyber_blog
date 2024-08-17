# Explosion

In this lab, we will be exposing vulnerable remote access tools on a Windows machine.

Perform a simple NMAP scan using the`-sV` switch.

<figure><img src="../../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>

We can try to get remote access to the target machine by running the xfreerdp remote access tool.

Use `xfreerdp /v:"Enter IP" /cert:ignore /u:Administrator` to attempt to gain administrator remote access to the Windows machine. When running this command, just hit enter to confirm the administrator is not configured with a password.

<figure><img src="../../.gitbook/assets/image (11) (1).png" alt=""><figcaption></figcaption></figure>

Once the remote desktop connection is established, you will find the flag located in the desktop folder.



References:

{% file src="../../.gitbook/assets/explosion_lab_guide.pdf" %}





&#x20;
