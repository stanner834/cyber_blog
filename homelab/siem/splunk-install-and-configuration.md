# Splunk install and configuration

This guide assumes that you already have Splunk installed on your machine, and you can access the GUI interface. If you have not downloaded the free version of Splunk, navigate to [https://www.splunk.com/en\_us/download.html](https://www.splunk.com/en\_us/download.html) to download.&#x20;

To start, we can head over to "forwarding and receving" under "Settings"

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Select "Add new" under "Receive data"

<figure><img src="../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

The default port Splunk listens on is 9997

<figure><img src="../../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

The next step will be to install a Splunk forwarder on our host.&#x20;

A `forwarder` is defined as a "Splunk Enterprise instance that forwards data to another Splunk Enterprise instance, such as an [indexer](https://docs.splunk.com/Splexicon:Indexer) or another forwarder, or to a third-party system."

{% embed url="https://www.splunk.com/en_us/download/universal-forwarder.html?locale=en_us" %}

<figure><img src="../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

The next steps will be to configure the Splunk forwarder on our machine of choice, in this example I will use my local Windows machine.

<figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

Generate credentials for your forwarder

<figure><img src="../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

You can complete the rest of the default settings

Next we will create an "inputs.conf" file in the C:\Program Files\SplunkUniversalForwarder\etc\system\local directory. In this input file we can add log source we would like to forward to our Splunk indexer.&#x20;

A Splunk `Indexer` is defined as "The repository for data. When the Splunk platform indexes raw data, it transforms the data into searchable [events](https://docs.splunk.com/Splexicon:Event)."

Add the following lines to your file to ingest Windows Event logs into Splunk:

`disabled=0`

`[WinEventLog://Security]`

`disabled=0`

`[WinEventLog://System]`

`disabled=0`

<figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

Navigate to your Splunk web interface and type `index=main` in the search bar to populate your Windows Event logs.&#x20;

<figure><img src="../../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

We can add a Microsoft Windows TA to automaitcally apply event types and tags to our logs. Navigate to "Apps", "Find More Apps". In the search bar type "Windows" and you will find the official TA.&#x20;

Select install to deploy to your Splunk instance.

<figure><img src="../../.gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>

If you would like your data to be CIM compliant, you can also install the Splunk Common Information Model TA as well. We will not go deeper into data models in this blog, but more information about CIM can be found at this link: [https://docs.splunk.com/Splexicon:CommonInformationModel](https://docs.splunk.com/Splexicon:CommonInformationModel)

<figure><img src="../../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (48).png" alt=""><figcaption><p>Example tstats search using the Endpoint data model</p></figcaption></figure>
