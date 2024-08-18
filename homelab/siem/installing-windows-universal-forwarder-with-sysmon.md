# Installing Windows Universal Forwarder with Sysmon

Download this link from Splunk

[https://www.splunk.com/en\_us/download/universal-forwarder.html?locale=en\_us](https://www.splunk.com/en\_us/download/universal-forwarder.html?locale=en\_us)

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

Naviage to the directory and run:

curl -o splunkforwarder-9.3.0-51ccf43db5bd-x64-release.msi "https://download.splunk.com/products/universalforwarder/releases/9.3.0/windows/splunkforwarder-9.3.0-51ccf43db5bd-x64-release.msi"



<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>



<figure><img src="../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>



<figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>



Navigate to ... directory



notepad.exe inputs.conf



<figure><img src="../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>



in bin directory type splunk restart



index=main host="TEST-RANGE-WIND"



You may have to open up firewall ports



curl -L -o Sysmon.zip https://download.sysinternals.com/files/Sysmon.zip



<figure><img src="../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

tar -xf Sysmon.zip



<figure><img src="../../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>



sysmon -i



<figure><img src="../../.gitbook/assets/image (9) (1).png" alt=""><figcaption></figcaption></figure>



<figure><img src="../../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>

