# Cribl Edge -> Splunk

In this blog, we will demonstrate how to send Cribl Edge logs to Splunk using the HTTP Event Collector (HEC). HEC is a Splunk feature that allows you to send data and application events to your Splunk deployment over HTTP or HTTPS protocols using token-based authentication.

To start, ensure you have a source ingesting logs of your choice. Refer to [this](cribl-edge-greater-than-splunk.md) blog to review how to set up log sources in Cribl. In this example, we are ingesting Windows Event logs into a Cribl Edge instance.

<figure><img src="../../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (61).png" alt=""><figcaption><p>Windows Event logs are currently being sent to "DevNull", a testing destination</p></figcaption></figure>

Navigate to your Splunk instance, go to "Settings" > "Indexes," and click "New index."

<figure><img src="../../.gitbook/assets/image (73).png" alt=""><figcaption></figcaption></figure>

Enter the index name as "Cribl," or choose a different name for your index.

<figure><img src="../../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

Next, we need to configure HEC in the Splunk console. Go to "Settings" > "Data inputs" and click on "HTTP Event Collector."

<figure><img src="../../.gitbook/assets/image (74).png" alt=""><figcaption></figcaption></figure>

Select "New token" in the upper right-hand corner.

<figure><img src="../../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

The name can be whatever you choose for the HEC connection; the other options can be left as default.

<figure><img src="../../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>

Next, select the "Cribl" index we created earlier, and define a new source type or use an existing one.

<figure><img src="../../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

Select "Review," then "Submit" to view your token. Copy this so we can use it in our Cribl instance.

<figure><img src="../../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

Navigate back to your Cribl Edge instance. Under "Destinations," select "HEC."

<figure><img src="../../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>

Click "Add destination."

<figure><img src="../../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>

Fill out the following details:

* **OutputID**: The name of your destination
* **HEC endpoint**: The IP address of your Splunk instance
* **Authentication method**: We will use "Manual" in this example
* **HEC auth token**: The token you copied in earlier steps

<figure><img src="../../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>

Complete the form and click "Save."

Go to the "Data Routes" section within Cribl, and create a new route with any name you desire. Fill out the following:

* **Route name**: The name you choose
* **Filter**: The log sources you want to allow through the route
* **Pipeline**: Select which pipeline you want to send the logs through; there is a default option for Windows Event logs
* **Output**: Select the name of the HEC destination you created in Cribl

<figure><img src="../../.gitbook/assets/image (81).png" alt=""><figcaption></figcaption></figure>

We can go back to Cribl Destinations to run a quick test signal.

<figure><img src="../../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>

Navigate to your Splunk search bar and type `index=cribl` to see the ingested logs.

<figure><img src="../../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>
