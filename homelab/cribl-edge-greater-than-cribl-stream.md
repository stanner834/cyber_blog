# Cribl Edge -> Cribl Stream

I have completed my Cribl user certification and wanted to showcase what I learned through a quick demo. The goal of this assignment was to run Cribl Edge on my local computer using WSL and Cribl Stream on a Virtual Machine in VirtualBox. I then wanted to forward the logs from Cribl Edge to Cribl Stream using the TCP JSON source/destination.

To start, navigate to "Sources" in Cribl Stream and add a source. By using 0.0.0.0 as the IP address, you are instructing Stream to listen to all incoming IPs. The default port used in this example is 10300. Make sure to generate an authentication token and save it for later. Click save and let's move forward.

<figure><img src="../.gitbook/assets/image (6) (1) (1) (1) (1).png" alt=""><figcaption><p>Add source in Cribl Stream</p></figcaption></figure>

Next, we must add a new source in our Cribl Edge instance. Navigate there and click "Exec" source. This allows you to run a command via CMD and display the logs. Type in a unique name, a command you would like to run, and an interval of your choice.

<figure><img src="../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>Adding a source in Cribl Edge</p></figcaption></figure>

Optionally, you can add event breakers to your source.

<figure><img src="../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>Add an event breaker</p></figcaption></figure>

In our Cribl Edge instance, we can add a destination to ensure the logs get sent to the Cribl Stream instance. Fill out the form accordingly, making sure to use the same authentication token generated in the Cribl Stream instance.

<figure><img src="../.gitbook/assets/image (7) (1) (1) (1).png" alt=""><figcaption><p>Add a destination to Cribl Edge</p></figcaption></figure>

To ensure the data we are generating from our source is being sent to our Cribl Stream instance, we need to deploy a route. Set the pipeline to "passthru" and ensure the output is the same input ID created when building the destination in Cribl Edge.

<figure><img src="../.gitbook/assets/image (8) (1) (1).png" alt=""><figcaption><p>Add a route in Cribl Edge</p></figcaption></figure>

Navigate to your Cribl Stream instance, in Sources > Live Data, click "Capture" and confirm that logs are coming in.

<figure><img src="../.gitbook/assets/image (6) (1) (1) (1).png" alt=""><figcaption><p>Confirm live data</p></figcaption></figure>

References:

{% embed url="https://docs.cribl.io/stream/usecase-edge-stream/" %}
