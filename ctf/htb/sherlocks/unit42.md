# Unit42

## UltraVNC Backdoor Analysis

This CTF focused on analyzing Windows Sysmon logs based on Palo Alto’s Unit42 research into a backdoored UltraVNC campaign. Using `EvtxECmd` to parse EVTX files and loading the CSV into ELK and Splunk allowed for quick searching and filtering of event data.

***

### Setup

{% embed url="https://ericzimmerman.github.io/#!index.md" %}

<figure><img src="../../../.gitbook/assets/image (141).png" alt=""><figcaption></figcaption></figure>

**Command to convert EVTX to CSV:**

```powershell
.\EvtxECmd.exe -f ..\unit42\Microsoft-Windows-Sysmon-Operational.evtx --csv .\output\
```

***

### Questions & Answers

> **Q: How many Event logs are there with Event ID 11?**\
> **A:** 56\
> (Event ID 11 indicates file creation.)

<figure><img src="../../../.gitbook/assets/image (140).png" alt=""><figcaption></figcaption></figure>

***

> **Q: What is the malicious process that infected the victim's system?**\
> **A:** `C:\Users\CyberJunkie\Downloads\Preventivo24.02.14.exe.exe`\
> (Event ID 1 captured process creation with command-line details.)

<figure><img src="../../../.gitbook/assets/image (139).png" alt=""><figcaption></figcaption></figure>

***

> **Q: Which Cloud drive was used to distribute the malware?**\
> **A:** Dropbox

<figure><img src="../../../.gitbook/assets/image (138).png" alt=""><figcaption></figcaption></figure>

***

> **Q: What was the timestamp changed to for the PDF file?**\
> **A:** `2024-01-14 08:10:06`\
> (Time stomping used for defense evasion.)

<figure><img src="../../../.gitbook/assets/image (143).png" alt=""><figcaption></figcaption></figure>

***

> **Q: Where was "once.cmd" created on disk?**\
> **A:** `C:\Users\CyberJunkie\AppData\Roaming\Photo and Fax Vn\Photo and vn 1.1.2\install\F97891C\WindowsVolume\Games\once.cmd`\
> (Identified in Event ID 11 logs in Splunk: `index="unit42" sourcetype="csv" once.cmd`)

<figure><img src="../../../.gitbook/assets/image (142).png" alt=""><figcaption></figcaption></figure>

***

> **Q: What domain name did it try to connect to?**\
> **A:** `www.example.com`\
> (Possible connectivity check or C2 beacon.)

<figure><img src="../../../.gitbook/assets/image (144).png" alt=""><figcaption></figcaption></figure>

***

> **Q: Which IP address did the malicious process try to reach out to?**\
> **A:** `93.184.216.34`

<figure><img src="../../../.gitbook/assets/image (145).png" alt=""><figcaption></figcaption></figure>

***

> **Q: When did the process terminate itself?**\
> **A:** `2024-02-14 03:41:58`\
> (Located using `EventID=5` which logs process termination.)

<figure><img src="../../../.gitbook/assets/image (146).png" alt=""><figcaption></figcaption></figure>
