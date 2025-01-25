# Table of contents

* [About me](README.md)
* [My Mission](my-mission.md)
* [License](license.md)

## Homelab

* [SIEM Architecture](homelab/siem-architecture/README.md)
  * [ELK installation](homelab/siem-architecture/elk-installation.md)
  * [Splunk install and configuration](homelab/siem-architecture/splunk-install-and-configuration.md)
  * [Forwarding Sysmon logs to Splunk](homelab/siem-architecture/forwarding-sysmon-logs-to-splunk.md)
  * [Cribl Edge -> Cribl Stream](homelab/siem-architecture/cribl-edge-greater-than-cribl-stream.md)
  * [Cribl Edge -> Splunk](homelab/siem-architecture/cribl-edge-greater-than-splunk.md)
  * [Cribl -> Amazon S3 bucket](homelab/siem-architecture/cribl-greater-than-amazon-s3-bucket.md)
* [Test range](homelab/test-range/README.md)
  * [Breach and Attack Simulation (BAS)](homelab/test-range/breach-and-attack-simulation-bas.md)
  * [Test range topology](homelab/test-range/test-range-topology.md)
  * [Install MITRE Caldera](homelab/test-range/install-mitre-caldera.md)
  * [Install Atomic Red team](homelab/install-atomic-red-team.md)
  * [WannaCry ransomware execution](homelab/test-range/wannacry-ransomware-execution.md)
* [Raspberry Pi](homelab/raspberry-pi/README.md)
  * [Cloudflare DDNS](homelab/cloudflare-ddns.md)
  * [OpenVPN on Raspberry Pi](homelab/openvpn-on-raspberry-pi.md)
  * [Pi-Hole](homelab/pi-hole.md)
  * [Raspberry Pi project ideas](homelab/raspberry-pi-project-ideas.md)
* [Privacy](homelab/privacy/README.md)
  * [Kasm workspaces](homelab/privacy/kasm-workspaces.md)
  * [Tails Linux](homelab/tails-linux.md)
  * [Whonix](homelab/privacy/whonix.md)
* [Proxmox](homelab/proxmox/README.md)
  * [Next steps](homelab/proxmox/next-steps.md)
  * [How to backup VM's in Proxmox](homelab/proxmox/how-to-backup-vms-in-proxmox.md)
  * [Nested Virtualization troubleshooting](homelab/proxmox/nested-virtualization-troubleshooting.md)

## Cybersecurity

* [Purple team content](cybersecurity/purple-team-content/README.md)
  * [Detecting Discovery commands](cybersecurity/purple-team-content/detecting-discovery-commands.md)
* [Detection As Code (DAC)](cybersecurity/detection-as-code-dac/README.md)
  * [Sigma CI/CD](cybersecurity/detection-as-code-dac/sigma-ci-cd.md)
  * [DAC with Elastic SIEM](cybersecurity/detection-as-code-dac/dac-with-elastic-siem.md)
* [Use case repositories](cybersecurity/use-case-repositories.md)
* [Frameworks](cybersecurity/frameworks.md)
* [Tools](cybersecurity/tools.md)
* [Online resources](cybersecurity/online-resources/README.md)
  * [MITRE](cybersecurity/online-resources/mitre.md)
  * [Splunk](cybersecurity/online-resources/splunk.md)
  * [Machine Learning](cybersecurity/online-resources/machine-learning.md)
  * [Ethical Hacking](cybersecurity/online-resources/ethical-hacking.md)
  * [Podcasts](cybersecurity/online-resources/podcasts.md)
  * [Threat Reports](cybersecurity/online-resources/threat-reports.md)
  * [Detection Engineering articles](cybersecurity/online-resources/detection-engineering-articles.md)

## CTF

* [Machines](ctf/machines/README.md)
  * [MongoDB](ctf/machines/mongodb.md)
  * [Explosion](ctf/machines/explosion.md)
  * [Lame](ctf/machines/lame.md)
  * [Preignition](ctf/machines/preignition.md)
  * [Jerry](ctf/machines/jerry.md)
  * [Synced](ctf/machines/synced.md)
  * [Appointment](ctf/machines/appointment.md)
  * [Blue](ctf/machines/blue.md)
  * [Sequel](ctf/machines/sequel.md)
  * [Netmon](ctf/machines/netmon.md)
* [PicoCTF](ctf/picoctf.md)

## Road to OSCP

* [Exploit tool definitions](road-to-ocsp/exploit-tool-definitions.md)
* [Cheat sheets](road-to-ocsp/cheat-sheets/README.md)
  * [tmux](road-to-ocsp/cheat-sheets/tmux.md)
  * [Linux](road-to-ocsp/cheat-sheets/linux.md)
* [Weekly progress](road-to-ocsp/weekly-progress/README.md)
  * [Learning levels](road-to-oscp/weekly-progress/learning-levels.md)
  * [Skill sheet #1 - Assessment (9/28/2024)](road-to-oscp/weekly-progress/skill-sheet-1-assessment-9-28-2024.md)
  * [Skill Sheet #2 (Continuous)](road-to-oscp/weekly-progress/skill-sheet-2-continuous/README.md)
    * [Week 1](road-to-oscp/weekly-progress/skill-sheet-2-continuous/week-1.md)
    * [Week 2](road-to-oscp/weekly-progress/skill-sheet-2-continuous/week-2.md)
    * [Week 3](road-to-oscp/weekly-progress/skill-sheet-2-continuous/week-3.md)
    * [Week 4](road-to-oscp/weekly-progress/skill-sheet-2-continuous/week-4.md)
    * [Week 5](road-to-oscp/weekly-progress/skill-sheet-2-continuous/week-5.md)
    * [Week 6](road-to-oscp/weekly-progress/skill-sheet-2-continuous/week-6.md)
    * [Week 7](road-to-oscp/weekly-progress/skill-sheet-2-continuous/week-7.md)
    * [Week 8](road-to-oscp/weekly-progress/skill-sheet-2-continuous/week-8.md)
    * [Week 9](road-to-oscp/weekly-progress/skill-sheet-2-continuous/week-9.md)
    * [Week 10](road-to-oscp/weekly-progress/skill-sheet-2-continuous/week-10.md)
    * [Week 11](road-to-oscp/weekly-progress/skill-sheet-2-continuous/week-11.md)
    * [Week 12](road-to-oscp/weekly-progress/skill-sheet-2-continuous/week-12.md)

## Scripts

* [Python](scripts/python/README.md)
  * [Elastic DAC pipeline](scripts/python/elastic-dac-pipeline.md)

## AI/ML

* [Tools](ai-ml/tools/README.md)
  * [Fabric](ai-ml/tools/fabric.md)
  * [Run Ollama locally](ai-ml/tools/run-ollama-locally.md)
  * [Using Ollama & Fabric to build Sigma rules](ai-ml/tools/using-ollama-and-fabric-to-build-sigma-rules.md)
* [Custom prompts](ai-ml/custom-prompts/README.md)
  * [Lessons Learned](ai-ml/custom-prompts/lessons-learned.md)
  * [Create Sigma rules](ai-ml/custom-prompts/create-sigma-rules.md)

## Cloud projects

* [Cloud Resume Challenge - AWS](cloud-projects/readme-copy.md)

## BOOK CLUB

* [Lists](book-club/lists.md)
