# Cribl -> Amazon S3 bucket

In this blog, we will learn how to send Cribl Edge logs to a data lake. The purpose of doing this is to store logs in a cost-effective, long-term storage solution without needing to use or store them in a SIEM. This approach allows for incident response investigations if needed, while avoiding the necessity of storing and analyzing the logs in a SIEM.

First, navigate to your AWS account. You can create a free account here.

Once logged into your account, type "S3" in the search bar and select the link.

<figure><img src="../../.gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>

Click "Create Bucket."

<figure><img src="../../.gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>

Enter the name of the bucket and leave the default options as they are.

<figure><img src="../../.gitbook/assets/image (85).png" alt=""><figcaption></figcaption></figure>

Click "Create bucket."

<figure><img src="../../.gitbook/assets/image (86).png" alt=""><figcaption></figcaption></figure>

Next, we need to navigate to an IAM profile and gather credentials.

<figure><img src="../../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>

Click on your user profile (you may need to create one).

<figure><img src="../../.gitbook/assets/image (88).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (89).png" alt=""><figcaption></figcaption></figure>

Navigate to "Security Credentials."

<figure><img src="../../.gitbook/assets/image (90).png" alt=""><figcaption></figcaption></figure>

Create an access key to be used by Cribl.

<figure><img src="../../.gitbook/assets/image (91).png" alt=""><figcaption></figcaption></figure>

You will be presented with some options for creating the access key. On the first page, select "Other."

<figure><img src="../../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>

Click "Next," enter a description if desired, and then create the access key.

<figure><img src="../../.gitbook/assets/image (93).png" alt=""><figcaption></figcaption></figure>

Copy your access key and secret key to be used within Cribl for authentication.

Now, go to the Cribl Edge console, and within "Destinations," select "S3."

<figure><img src="../../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>

Click "Add Destination."

<figure><img src="../../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>

Fill out the output ID field with the name of the destination and enter the exact bucket name you created in the AWS console earlier.

<figure><img src="../../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>

Next, select "Authentication" in the tab below. Choose "Manual" as your authentication method, and copy and paste the access key and secret key created for your AWS user profile.

<figure><img src="../../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>

Then, navigate to "Data Routes." You can create a new route by selecting "Add Route." Add a route name, and enter "True" to allow all logs from this Cribl Edge instance to go through this route. Select the passthru pipeline to avoid any pre-processing of the data before it is sent to S3. Ensure you select the output ID you created in the S3 destination section. If you have any data routes before this route, make sure it is not set to "final" to allow for data flow.

<figure><img src="../../.gitbook/assets/image (98).png" alt=""><figcaption></figcaption></figure>

Navigate back to the S3 bucket, and you should see a folder containing your endpoint logs.

<figure><img src="../../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>

You can always test by going to your destination and selecting the "Test," "Status," or "Live Data" tabs in that view.

<figure><img src="../../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>
