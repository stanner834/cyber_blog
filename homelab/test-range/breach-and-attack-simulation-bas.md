# Breach and Attack Simulation (BAS)

Breach and Attack Simulation (BAS) is a technology that enables organizations to continuously and automatically simulate cyberattacks, replicating the tactics, techniques, and procedures (TTPs) used by real-world threat actors. BAS tools are designed to test and assess the effectiveness of an organization’s security controls, helping identify vulnerabilities and weaknesses in their defenses before an actual attack occurs.

We are going to use MITRE Caldera to run a few tests against a Windows 11 machine and review the results. If you haven't already, read ["Install MITRE Caldera" ](install-mitre-caldera.md)to get started.

MITRE Caldera comes with preconfigured "Adversaries" that have a set of abilities. An ability within Caldera is a test script that performs a malicious action you would like to test on your machine. Many of the tests actually come from the Atomic Red Team repository. Within MITRE Caldera, you can review all abilities by selecting the "Ability" tab, and you can review all threat actors by clicking the "Adversaries" tab. One of the best aspects of MITRE Caldera is the ability to create your own abilities and adversaries, as it is open source. New adversaries can be created based on MITRE TTP mappings.

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption><p>Caldera abilities</p></figcaption></figure>

To get started, let's select the "Discovery" Adversary profile.

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>Adversary profiles</p></figcaption></figure>

Your screen should populate with all the abilities associated with this Adversary profile. From this pane, you have the option to add more abilities if you'd like. Next, let's click "Operations."

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

An operation is a test we create based on an adversary profile. To create a new operation, select "Create Operation."

<figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

Name your operation and make sure to select the "Discovery" Adversary profile. From here, we can leave the rest of the settings as default and select "Start" to kick off the test on our machine (using the Sandcat agent we installed during the setup phase). There will be 12 total tests running from this threat actor.

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>

You can select "View Command" or "View Output" to get more details about what is seen in the terminal.

<figure><img src="../../.gitbook/assets/image (7) (1).png" alt=""><figcaption></figcaption></figure>

After testing is complete, we can add any manual commands we would like. I am going to use "whoami" as another discovery command.

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

After normal red team operations, we would like to do a debrief with the blue team to gather necessary details, identify what we may have missed, and discuss best practices moving forward. Navigate to "Debrief" to get a graphical depiction of your attack.

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

You can also view agents, steps, tactics & techniques, and a fact graph—very helpful information. We want to download the debrief to send over to our blue team, so select "Download PDF Report."

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

When opening the report, we get very detailed information about the test, including attack graphs and commands run.

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

This information is incredibly helpful for a blue team member. Another very cool feature is the ability to create MITRE ATT\&CK mappings from the "Compass" page. If you select "Discovery" in the "Select an Adversary" box and click "Generate Layer," it will create a JSON file for you to download and upload into a MITRE matrix.

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

See the highlighted techniques for the commands that were just run.

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

You can also create your own MITRE ATT\&CK layer and select "Create Operation" for Caldera to build a custom operation aligned to the TTPs you highlighted in the matrix. Just go back to the "Adversaries" tab and select "Import" to import your MITRE JSON file.

<figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (111).png" alt=""><figcaption></figcaption></figure>
