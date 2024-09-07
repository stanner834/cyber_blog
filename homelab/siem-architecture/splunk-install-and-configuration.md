# Splunk install and configuration

Splunk is a Security Information and Event Management (SIEM) platform designed to search, monitor, and analyze machine-generated data in real-time. It helps organizations transform raw data from various sources, such as logs and events, into valuable insights, enabling them to troubleshoot issues and enhance security. In this blog, we will install and configure Splunk Enterprise on our machine, and then deploy a universal forwarder to capture and send Windows event logs to our Splunk instance.

This guide assumes that you already have Splunk installed on your machine and can access the GUI interface. If you haven't downloaded the free Enterprise version of Splunk, go to https://www.splunk.com/en\_us/download.html to download it.

To start, go to "Forwarding and Receiving" under "Settings."

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Select "Add new" under "Receive data."

<figure><img src="../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

The default port Splunk listens on is 9997.

<figure><img src="../../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

Next, install a Splunk forwarder on your host. A forwarder is defined as a "Splunk Enterprise instance that forwards data to another Splunk Enterprise instance, such as an indexer or another forwarder, or to a third-party system."

{% embed url="https://www.splunk.com/en_us/download/universal-forwarder.html" %}

<figure><img src="../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

If you are using a Windows machine, execute the .msi file in your directory of choice, and accept the the default configuration settings.&#x20;

<figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

Next, create an "inputs.conf" file in the `C:\Program Files\SplunkUniversalForwarder\etc\system\local` directory. In this input file, you can add the log sources you want to forward to your Splunk indexer. A Splunk indexer is defined as "the repository for data. When the Splunk platform indexes raw data, it transforms the data into searchable events."

<figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

Add the following lines to your file to ingest Windows Event logs into Splunk:

```
disabled=0
[WinEventLog://Security]
disabled=0
[WinEventLog://System]
disabled=0
```

Navigate to your Splunk web interface and type `index=main` in the search bar to populate your Windows Event logs.

<figure><img src="../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

You can add a Microsoft Windows Technical Add-On (TA) to automatically apply event types and tags to your logs. Navigate to "Apps," then "Find More Apps." In the search bar, type "Windows," and you will find the official TA. Select "Install" to deploy it to your Splunk instance.

<figure><img src="../../.gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>

If you want your data to be CIM compliant, you can also install the Splunk Common Information Model TA. We will not go deeper into data models in this guide, but more information about CIM can be found at this link: https://docs.splunk.com/Splexicon:CommonInformationModel.

<figure><img src="../../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>
