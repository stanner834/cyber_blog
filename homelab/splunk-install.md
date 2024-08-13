# Splunk setup & Purple teaming

Install CIM data model

Upload data

Get Cribl stream data



<figure><img src="../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

{% embed url="https://www.splunk.com/en_us/download/universal-forwarder.html?locale=en_us" %}

<figure><img src="../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>



<figure><img src="../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

`index=main source="WinEventLog:Security" signature="A security-enabled local group membership was enumerated"`

<figure><img src="../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>



stann@stann:\~$ wget -O splunkforwarder-9.3.0-51ccf43db5bd-linux-2.6-amd64.deb "https://download.splunk.com/products/universalforwarder/releases/9.3.0/linux/splunkforwarder-9.3.0-51ccf43db5bd-linux-2.6-amd64.deb" --2024-08-11 01:45:04-- https://download.splunk.com/products/universalforwarder/releases/9.3.0/linux/splunkforwarder-9.3.0-51ccf43db5bd-linux-2.6-amd64.deb Resolving download.splunk.com (download.splunk.com)... 18.161.134.34, 18.161.134.21, 18.161.134.116, ... Connecting to download.splunk.com (download.splunk.com)|18.161.134.34|:443... connected. HTTP request sent, awaiting response... 200 OK Length: 42488486 (41M) \[binary/octet-stream] Saving to: ‘splunkforwarder-9.3.0-51ccf43db5bd-linux-2.6-amd64.deb’

splunkforwarder-9. 100%\[================>] 40.52M 26.3MB/s in 1.5s

2024-08-11 01:45:06 (26.3 MB/s) - ‘splunkforwarder-9.3.0-51ccf43db5bd-linux-2.6-amd64.deb’ saved \[42488486/42488486]

stann@stann:\~$

{% embed url="https://github.com/stanner834" %}

