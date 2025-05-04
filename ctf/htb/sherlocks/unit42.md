# Unit42

To get the logs in proper format to be analyze, we need to use a tool that can parse the evtx files and upload them into our SIEM of choice, which today I will be using ELK.&#x20;

{% embed url="https://ericzimmerman.github.io/#!index.md" %}

```
.\EvtxECmd.exe -f ..\unit42\Microsoft-Windows-Sysmon-Operational.evtx --csv .\output\
```

<figure><img src="../../../.gitbook/assets/image (141).png" alt=""><figcaption></figcaption></figure>

In this Sherlock, you will familiarize yourself with Sysmon logs and various useful EventIDs for identifying and analyzing malicious activities on a Windows system. Palo Alto's Unit42 recently conducted research on an UltraVNC campaign, wherein attackers utilized a backdoored version of UltraVNC to maintain access to systems. This lab is inspired by that campaign and guides participants through the initial access stage of the campaign.

How many Event logs are there with Event ID 11?

56

```
EventId : 11
```

<figure><img src="../../../.gitbook/assets/image (140).png" alt=""><figcaption></figcaption></figure>

Whenever a process is created in memory, an event with Event ID 1 is recorded with details such as command line, hashes, process path, parent process path, etc. This information is very useful for an analyst because it allows us to see all programs executed on a system, which means we can spot any malicious processes being executed. What is the malicious process that infected the victim's system?

C:\Users\CyberJunkie\Downloads\Preventivo24.02.14.exe.exe

```
EventId : 1
```

<figure><img src="../../../.gitbook/assets/image (139).png" alt=""><figcaption></figcaption></figure>

Which Cloud drive was used to distribute the malware?

Dropbox

<figure><img src="../../../.gitbook/assets/image (138).png" alt=""><figcaption></figcaption></figure>

Switching over to Splunk just for the fun...I think it is a little more flexible using SPL than KQL.

For many of the files it wrote to disk, the initial malicious file used a defense evasion technique called Time Stomping, where the file creation date is changed to make it appear older and blend in with other files. What was the timestamp changed to for the PDF file?

`2024-01-14 08:10:06`

<figure><img src="../../../.gitbook/assets/image (143).png" alt=""><figcaption></figcaption></figure>

The malicious file dropped a few files on disk. Where was "once.cmd" created on disk? Please answer with the full path along with the filename.

`index="unit42" sourcetype="csv" once.cmd`

<figure><img src="../../../.gitbook/assets/image (142).png" alt=""><figcaption></figcaption></figure>

