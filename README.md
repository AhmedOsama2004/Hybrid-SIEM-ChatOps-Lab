# Hybrid SIEM Architecture & ChatOps Ticketing Pipeline

## Project Overview
This project demonstrates the architecture and deployment of a unified Security Operations Center (SOC) monitoring ecosystem. The lab provides continuous security visibility across two completely distinct attack surfaces: corporate internal endpoints (**Windows 10 Workstation via Sysmon**) and public-facing corporate infrastructure (**DVWA Web Application**). 

Instead of relying on passive, siloed dashboards, this architecture features an automated **ChatOps Alerting Pipeline** using customized Python integrations to forward critical telemetry directly to **Discord Webhooks**, transforming a communication channel into a real-time incident ticketing center.

---

## Key Features & Detections
* **Endpoint Telemetry Enrichment:** Deployed **Sysmon** alongside standard Windows Security Logs to unlock low-level operational visibility.
* **Web Threat Identification:** Captured malicious application-layer events (SQL Injection, Authentication Brute Forcing) targetting **DVWA**.
* **MITRE ATT&CK Mapping:** All custom rules are coded to align directly with modern adversarial techniques.
* **Automated ChatOps Tickets:** High-severity indicators skip the console queue and populate a dedicated Discord incident triage channel instantly.

---

## System Architecture

```text
[ Windows 10 Endpoint ]   ---> Ingests Logs via Agent ---> [  Wazuh SIEM  ] ---> Discord Webhook ---> [ Discord Ticketing Channel ]
(Sysmon & Registry FIM)                                      [   Manager    ]
                                                                  ^
[  DVWA Web Server    ]   ---> Parses Apache Logs     ---> -------|
(SQLi & Login Audits)
