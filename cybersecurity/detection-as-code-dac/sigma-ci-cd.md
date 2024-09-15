# Detection As Code (DAC)

Detection as Code (DaC) is the practice of writing, managing, and maintaining security detection rules and logic in a version-controlled, code-like format. Similar to how infrastructure is defined and managed as code (Infrastructure as Code), Detection as Code applies software development principles to security detections, allowing teams to create, test, and deploy detection rules in a consistent, scalable, and automated manner.

Key features of Detection as Code include:

**Version Control:** Detection rules are stored in version control systems like Git, enabling teams to track changes, roll back to previous versions, and collaborate more effectively. This also improves auditability, allowing teams to see who made changes and why.

**Automation:** By integrating detection rules into Continuous Integration/Continuous Deployment (CI/CD) pipelines, security teams can automate the testing and deployment of new or updated detection rules. This reduces manual overhead and helps ensure that changes don’t break existing detections.

**Collaboration and Review:** DaC promotes collaboration between security teams, developers, and other stakeholders by enabling code reviews and discussions around detection logic. This improves the quality and accuracy of detections while reducing the chances of false positives or negatives.

**Standardization:** Using code to define detections ensures consistency across environments and teams, as rules can be written in standardized formats (e.g., Sigma) and applied across multiple platforms (e.g., SIEMs, EDR solutions).

**Scalability:** With the ability to manage rules as code, organizations can efficiently scale their detection capabilities across multiple environments, ensuring that detection logic remains consistent and up-to-date across various systems.

In practice, Detection as Code is used to create and manage security detections that monitor for specific attack patterns, behaviors, or anomalies. For example, a security team may write a rule in YAML format to detect unusual logins or privilege escalations, and then commit that rule to a Git repository. Automated systems will then validate, test, and deploy the rule to a SIEM or other detection tool. This approach allows organizations to keep pace with evolving threats while maintaining the flexibility and agility needed in modern cybersecurity environments.

To begin, we will use the Sigma rule we created in "Detecting Discovery Commands" as an example of DaC.

<figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

Within source control, we can see the "Commit" button to commit changes to our Git branch. First, you must stage the changes on the right-hand side, choose a name for the commit message, and select "Commit."

<figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

After committing, we can sync the changes with our main remote branch.

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

In my remote main branch, we can see the rule has been successfully synced.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Clone my GitHub repository to use my Detection Engineering content:

`git clone` [`https://github.com/stanner834/Detection_Engineering_Content.git`](https://github.com/stanner834/Detection\_Engineering\_Content.git)

{% embed url="https://github.com/stanner834/Detection_Engineering_Content/blob/main/wmic_query_for_antivirus.yml" %}
