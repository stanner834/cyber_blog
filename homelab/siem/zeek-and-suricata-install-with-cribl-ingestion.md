# Zeek & Suricata install with Cribl ingestion

root@DELLSAMTANNER:/opt/zeek/share/zeek/site# ls local.zeek root@DELLSAMTANNER:/opt/zeek/share/zeek/site# nano local.zeek root@DELLSAMTANNER:/opt/zeek/share/zeek/site#



af-packet:

* interface: eth3

community-id: true



default-rule-path: /var/lib/suricata/rules

rule-files:

* suricata.rules

sudo suricata-update



root@DELLSAMTANNER:/var/lib# sudo systemctl start suricata.service root@DELLSAMTANNER:/var/lib# sudo systemctl status suricata.service



sudo suricata-update list-sources



oot@DELLSAMTANNER:/var/log/suricata# sudo suricata-update enable-source malsilo/win-malware



root@DELLSAMTANNER:/var/log/suricata# sudo suricata -T -c /etc/suricata/suricata.yaml -v



alert icmp any any -> $HOME\_NET any (msg:"ICMP Ping"; sid:1; rev:1;)



08/11/2024-13:57:40.156339 \[**] \[1:2100498:7] GPL ATTACK\_RESPONSE id check returned root \[**] \[Classification: Potentially Bad Traffic] \[Priority: 2] {TCP} 18.238.152.55:80 -> 192.168.1.208:60842 08/11/2024-13:58:10.339345 \[**] \[1:1:1] ICMP Ping \[**] \[Classification: (null)] \[Priority: 3] {ICMP} 142.250.115.138:0 -> 192.168.1.208:0

<figure><img src="../../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (14) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (4) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% embed url="https://www.youtube.com/watch?v=UXKbh0jPPpg" %}

{% embed url="https://www.youtube.com/watch?v=-VojasmHz70" %}

{% embed url="https://www.youtube.com/watch?v=QiV_wviNYJg" %}

{% embed url="https://www.youtube.com/watch?v=Oc1FxJXETF0" %}

{% embed url="https://github.com/lameCreations/Zeek_Install_Instructions/blob/main/README.md" %}
