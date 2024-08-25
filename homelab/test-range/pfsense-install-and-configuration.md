# Pfsense install and configuration



<figure><img src="../../.gitbook/assets/image (11) (1) (1).png" alt=""><figcaption></figcaption></figure>

Set three interfaces, one for NAT and two for internal networks

Click start

Run through all default options



Eject the disk and reset the machine

<figure><img src="../../.gitbook/assets/image (12) (1) (1).png" alt=""><figcaption></figcaption></figure>



<figure><img src="../../.gitbook/assets/image (13) (1) (1).png" alt=""><figcaption></figcaption></figure>



Start another virtual machine and assign it to inet or internal Network so you can connect to Pfsense

I personally run Ubuntu desktop



Check the ip address



<figure><img src="../../.gitbook/assets/image (13) (1).png" alt=""><figcaption></figcaption></figure>

Default credentials are admin and pfsense

<figure><img src="../../.gitbook/assets/image (14) (1).png" alt=""><figcaption></figcaption></figure>



<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

Finish the installation and viola!



<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>



<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Access rules.emergingthreats.net



<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

Click save

<figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

Set rule threshold to 1 hour



<figure><img src="../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>



Update all the rules



<figure><img src="../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

You can change rule updates to happen once per day



<figure><img src="../../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>

**Alerts** will still be sent and logged if they meet or exceed the configured priority level (`NOTICE` in this case). Since alerts are usually of a higher severity, they will still be logged even if the priority is set to `NOTICE`.



Leave the rest of the settings as default and click save.



In the settings menu, select "LAN categories" and "select all"



&#x20;

<figure><img src="../../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (11) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (12) (1).png" alt=""><figcaption></figcaption></figure>

{% embed url="https://www.youtube.com/watch?v=S0-vsjhPDN0&t=285s" %}

{% embed url="https://www.youtube.com/watch?v=LX-Y-99zJ3M" %}
