# Install MITRE Caldera

## Caldera

MITRE Caldera is an open-source platform designed for adversary emulation and red team exercises. It allows organizations to emulate the tactics, techniques, and procedures (TTPs) used by real-world advanced persistent threats (APTs) and other sophisticated attackers. This enables defenders to test their response plans and procedures without the need for a complex emulation environment.

### Key Features and Use Cases

* **Autonomous Adversary Emulation**: Caldera can autonomously simulate breach-and-attack scenarios, mimicking real-world attacker behavior.
* **Manual Red-Team Engagements**: The platform also supports manual red team exercises, where human operators conduct simulated attacks.
* **Automated Incident Response**: Caldera automates incident response activities, helping organizations assess their response capabilities and identify areas for improvement.
* **Endpoint Security Testing**: The platform can test endpoint security solutions and evaluate a network’s security posture against common post-compromise adversarial techniques.
* **Operational Technology (OT) Emulation**: Caldera includes extensions for OT environments, enabling security teams to emulate attacks on industrial control systems and assess their security posture.

### Benefits

* **Reduced Resource Requirements**: Caldera automates many aspects of adversary emulation, allowing security teams to focus on more complex testing.
* **Improved Incident Response**: The platform helps organizations assess and enhance their incident response capabilities, reducing the time and effort needed to respond to real-world attacks.
* **Enhanced Threat Intelligence**: Caldera offers insights into adversary behavior, enabling defenders to better understand and prepare for emerging threats.
* **Compliance and Assurance**: The platform can help demonstrate compliance with regulatory requirements and assurance standards, such as the NIST Cybersecurity Framework.

### Installation

You can download MITRE Caldera and run exercises on your own machine. If you're using Kali Linux, it's as simple as running:

```bash
sudo apt install caldera
```

To start Caldera, run:

```bash
caldera --insecure
```

Then, open a web browser and navigate to `localhost:8888`. The default credentials are:

* **Red team**: `Red:Admin`
* **Blue team**: `Blue:Admin`

<figure><img src="../../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>

### Deploying an Agent

First, deploy an agent by navigating to the "Agent" tab on the left and selecting "Deploy an Agent."

<figure><img src="../../.gitbook/assets/image (106).png" alt=""><figcaption></figcaption></figure>

There are several agent types available. For this example, we'll continue with the default install option, Sandcat, which communicates via HTTP. Since I am using a Windows machine, I will select Windows, enter the IP of my local machine, and specify the name of the agent to be installed.

<figure><img src="../../.gitbook/assets/image (107).png" alt=""><figcaption></figcaption></figure>

Copy and paste the command into the terminal of the device where you want to install the agent. After executing the commands, you should see the agent's health appear in the "Agents" tab.

<figure><img src="../../.gitbook/assets/image (108).png" alt=""><figcaption></figcaption></figure>

Now, MITRE Caldera is installed and ready to run on your machine.

## References

{% embed url="https://caldera.mitre.org/" %}

{% embed url="https://www.kali.org/tools/caldera/" %}

{% embed url="https://github.com/mitre/caldera" %}
