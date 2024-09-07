# Breach and Attack Simulation (BAS)

Breach and Attack Simulation (BAS) is a technology that enables organizations to continuously and automatically simulate cyberattacks, replicating the tactics, techniques, and procedures (TTPs) used by real-world threat actors. BAS tools are designed to test and assess the effectiveness of an organization’s security controls, helping identify vulnerabilities and weaknesses in their defenses before an actual attack occurs.&#x20;

We are going to use MITRE Caldera to run a couple tests against a Windows 11 machine, and review the results.&#x20;

If you have not already, read [Install MITRE Caldera](install-mitre-caldera.md) to get started.&#x20;



MITRE Caldera comes with preconfigured "Adversaries" that have a set of abilities. An ability within Caldera is a test script that performs a malicious action you would like to test on your machine. Many of the tests actually come from the Atomic Red team repository. Within MITRE Caldera, you can review all abilities by selecting the "Ability" tab, and you can review all threat actors by clicking the "adversaries" tab. The best part about MITRE Caldera is the ability to create your own abilities and adversaries because it is open source. New adversaries can be created based on MITRE TTP mappings.&#x20;

&#x20;

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption><p>Caldera abilities</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Adversary profiles</p></figcaption></figure>

To get started, let's select the "Discovery" Adversary profile.&#x20;

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Your screen should populate all the abilities associated with this Adversary profile. From this pane you have the ability to add any more abilities if you would like to.&#x20;

Next lets click "Operations".

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

An operation is a test we create based on an adversary profile. To create a new operation, select "create operation".

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Name your operation, and make sure to select the "Discovery" adversary profile. From here we can leave the rest of the settings as default and select "Start" to kick of the test on our machine. (Sandcat agent we installed in the setup phase). There will be 12 total tests running from this threat actor.&#x20;

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

You can select "view command" or "view output" to get more details about what is seen in the terminal.&#x20;

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

After testing is complete, we can add any manual command we would like. I am going to use "whoami" as another discovery command.&#x20;

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

After normal red team operations, we would like to do a debriek with the Blue team to gather necessary details to identify what we may have missed and best practices moving forward. Navigate to "Debrief" to get a graph depiction of your attack.&#x20;

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

You can also view agents, steps, tactics & techniques, and a fact graph. Very helpful stuff.&#x20;

We want to download the debrief to send over to our blue team, so select "Download PDF report".

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

When opening the report we get very detailed information about the test, including attack graps and commands run.

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

This information is incredibly helpful for a blue team member.&#x20;

Another very cool feature is the ability to create MITRE ATT\&CK mappings from the "compass" page. If you select Discovery in the "Select an Adversary" selection box and click "Generate layer" it will create a json file for your to download and upload into a MITRE matrix.

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

See the highlighed techniques for commands that were just run.

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

You can also create your own MITRE ATT\&CK layer and select create operation for Caldera to built a custom operation aligned to the TTP's you highlighted in the matrix. Just go back to the "Adversaries" tab and select "import" to import your MITRE json file.&#x20;

<figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (111).png" alt=""><figcaption></figcaption></figure>
