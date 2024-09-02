# Cribl Edge -> Splunk

In this blog, we are going to demonstrate sending Cribl Edge logs to Splunk using HTTP Event Collector (HEC). HEC is a Splunk feature that allows you to send data and application events to your Splunk deployment over HTTP or HTTPS protocols using token-based authentication.



To start ensure you have a source ingesting a logs of your choice. Refer to [this](cribl-edge-greater-than-cribl-stream.md) blog to freshen up on setting up log sources in Cribl. In this example, we can see I am currently ingesting Windows Event logs to my Cribl Edge instance.

<figure><img src="../../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (61).png" alt=""><figcaption><p>Windows Event logs are currently being sent to "DevNull", a testing destination</p></figcaption></figure>

Navigate to your Splunk instance, and within "Settings" > "Indexes" click "New index".

<figure><img src="../../.gitbook/assets/image (73).png" alt=""><figcaption></figcaption></figure>

Type in the index name as Cribl, or whatever name you would like to use for your index.

<figure><img src="../../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

Next we need to configure HEC in the Splunk console. Navigate to "Settings" > "Data inputs" and click on "HTTP event collector"

<figure><img src="../../.gitbook/assets/image (74).png" alt=""><figcaption></figcaption></figure>

Select "New token" in the upper right hand corner.

<figure><img src="../../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

The name can be whatever you would like to call the HEC connection, the rest of the options can be left as default.

<figure><img src="../../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>

Next we can select the "Cribl" index we created earlier, and also define a new source type or use an existing one.

<figure><img src="../../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

Select review, then submit to see your token. Copy this so we can use it in our Cribl instance.

<figure><img src="../../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

Navigate back to our Cribl Edge instance. Under destinations select "HEC".

<figure><img src="../../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>

Select "Add destination"

<figure><img src="../../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>

We need to fill out the following:

* OutputID: The name of your destination
* HEC endpoint: The IP address of your Splunk instance
* Authentication method: We will be using manual in this example
* HEC auth token: The token you copied in earlier steps

Fill out the form and select "save"

<figure><img src="../../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>

Go to the "Data routes" section within Cribl, create a new route with any name you desire. We can fill out as follows:

* Route name: The name you would like to choose
* Filter: The log sources you would like to allow through the route
* Pipeline: Select which pipeline you would like to send the logs through, there is a default option for Windows Event logs
* Output: Select the name of the HEC destination you created in Cribl

<figure><img src="../../.gitbook/assets/image (81).png" alt=""><figcaption></figcaption></figure>

We can go back to Cribl Destinations to run a quick test signal.&#x20;

<figure><img src="../../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>

Navigate to your Splunk search bar, type `index=cribl` to see the ingested logs.

<figure><img src="../../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>
