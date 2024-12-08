# Using Ollama & Fabric to build Sigma rules

In this blog we are going to learn how to use an oper source LLM (Ollama) to build SIgma rules. First we will run tests, analyze the logs in Splunk, and run a command to build our sigma from the Splunk raw log we identified.

Step 1: Collect Data

Start by gathering detailed network information from your Windows machine using the following commands:

1. **`ipconfig /all`**\
   This command provides comprehensive details about all network interfaces, including IP addresses, DNS servers, and other configuration settings.
2. **`netsh interface show interface`**\
   Use this command to view the status of network interfaces, including whether they are enabled or disabled and their current state.
3. **`arp -a`**\
   Display the ARP (Address Resolution Protocol) table, which maps IP addresses to MAC addresses on the local network.
4. **`nbtstat -n`**\
   Show the NetBIOS name table for the local computer, which is useful for troubleshooting network name resolution issues.
5. **`net config`**\
   View the configuration of the local network services, including network-related settings.

<figure><img src="../../.gitbook/assets/image (112).png" alt=""><figcaption></figcaption></figure>

#### Step 2: Analyze raw Logs in Splunk

Use the following Splunk search command to view the raw log data:

```spl
index=* netsh interface show interface | table _raw
```

This command searches for logs within the specified index and displays the raw log data in a table format. Copy the raw log data for the next step.

#### [Step 3: Install and Configure Fabric](fabric.md)

To automate the process of creating Sigma rules, you need to have Fabric installed and configured. Fabric is an automation tool that can streamline various tasks.

#### [Step 4: Install Ollama](run-ollama-locally.md)

Ensure that Ollama is installed. Ollama is used to build Sigma rules from raw log data. Refer to the installation instructions to ensure Ollama is correctly configured on your machine.

#### Step 5: Create Sigma Rules

With Fabric and Ollama set up, you can now create Sigma rules from your raw log data. Use the following command to process the data and generate Sigma rules:

```bash
pbpaste | fabric --pattern create_sigma_rules --model llama3.1:8b --stream
```

This command performs the following actions:

* **`pbpaste`**: Retrieves the raw log data from your clipboard.
* **`fabric --pattern create_sigma_rules`**: Uses Fabric to process the data and create Sigma rules.
* **`--model llama3.1:8b`**: Specifies the model to be used by Fabric for rule creation.
* **`--stream`**: Indicates that the data should be processed in streaming mode.

<figure><img src="../../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (113).png" alt=""><figcaption><p>Using GPT-4o-Mini</p></figcaption></figure>

After running the command, review the output of the model. You can then copy and paste the generated Sigma rule into your text editor or SIEM (Security Information and Event Management) system of choice.

<figure><img src="../../.gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>
