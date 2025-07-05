# Microsoft Sentinel IR practice

## Brute Force attempts

![IR-Azure-1](https://github.com/user-attachments/assets/800154a8-7b39-4fc8-8aed-232f4461460a)

### Summary

![IR-Azure-2](https://github.com/user-attachments/assets/8b9a8559-f241-4db2-849e-d7dc2bdfa0f9)

Incident Report – CUSTOM: Brute Force ATTEMPT - Windows

Incident ID: 72

Date/Time: May 3, 2025 – 11:44:58

Asset: Windows Virtual Machine (Windows-vm)

Source IP: 102.88.21.212

Duration: Approx. 20 minutes

A brute force attack was detected against the Administrator account on the Windows virtual machine. The attack originated from IP address 102.88.21.212 and spanned approximately 20 minutes. All login attempts failed, with no evidence of successful authentication.
Investigation Details
Security Event Logs confirm repeated Event ID 4625 (failed logon attempts) from the source IP.
The following KQL query was used to verify the activity:

     SecurityEvent
     | where EventID == 4624 
     | where IPAddress == "102.88.21.212"

Threat Intelligence Summary:

VirusTotal: 7/94 engines flagged the IP as malicious.

BrightCloud: High Risk.

Cisco Talos: Neutral IP reputation.

AbuseIPDB: Reported 81 times, Confidence of Abuse: 100%.

ScamAnalytics: Fraud Score: 79.

DNSlytics: Listed on DNS blacklist. No domains/mail servers hosted.

Correlations:

![IR-Azure-3](https://github.com/user-attachments/assets/ff01dcdb-cbb5-44ef-a488-83cdb65a3837)
![IR-Azure-4](https://github.com/user-attachments/assets/fc02b71d-75bc-489b-91dd-6a8a9ebc7f19)
![IR-Azure-5](https://github.com/user-attachments/assets/c1429ae9-94a6-413b-a7a0-e5cc55ed8949)

The IP is involved in 42 separate incidents.
The attacker profile is linked to 4 additional alerts across the environment.

### Conclusion and Response
Although the activity was clearly malicious, no compromise occurred. All authentication attempts failed. It is important to note that the firewall and NSG (Network Security Group) were intentionally disabled as part of the honeynet simulation environment, allowing this kind of traffic.

Action Taken:

- This incident has been closed as a false positive in the context of the test environment. However, security controls will be re-enabled.
