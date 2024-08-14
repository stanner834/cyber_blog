# Enable Sysmon logs in Windows

Download Sysmon from the Windows site

{% embed url="https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon" %}

Navigate to the install directory

<figure><img src="../../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>

.\Sysmon64.exe -accepteula -i

<figure><img src="../../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>

Navigate to windows Event Viewer

Microsoft/Windows/Sysmon/Operational



See other log types that you can ingest here

<figure><img src="../../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>

.\Sysmon64.exe -c

.\Sysmon64.exe -? config

{% embed url="https://www.youtube.com/watch?v=B7Lf-IWVa5I" %}
