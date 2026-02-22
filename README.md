# 🛡️ Enterprise SOC Home Lab: pfSense & Wazuh

## 📖 Project Objective
The goal of this project is to build a functional Security Operations Center (SOC) home lab for Defensive Security (Blue Teaming). This environment integrates a pfSense network firewall with a Wazuh SIEM to capture network traffic, apply threat intelligence, and automatically block malicious inbound and outbound connections.

## 🏗️ Network Architecture
[Insert a screenshot of your network topology here if you have one]
* **Firewall:** pfSense (Virtual Machine)
* **SIEM:** Wazuh Manager (Ubuntu Host)
* **Endpoint:** Windows 10 (Virtual Machine on LAN Segment)

## 🚀 Phase 1: SIEM Log Integration (Completed)
In this phase, the firewall was successfully configured to send its logs to the central SIEM for analysis.
* Configured a dedicated LAN segment and assigned a static IP (192.168.1.10) to the Windows endpoint.
* Configured pfSense to forward remote Syslog traffic over port 5140 to the Wazuh Manager.
* Wrote a custom Wazuh XML decoder and rule (Rule ID: 100050) using `<match>filterlog</match>`.
* Successfully captured and visualized dropped firewall packets inside the Wazuh dashboard.

## 🌍 Phase 2: Threat Intelligence & Geo-Blocking (Completed)
In this phase, the firewall was upgraded with a threat intelligence feed to reduce alert fatigue by automatically dropping traffic from high-risk countries.
* Performed a safe OS upgrade on the pfSense firewall.
* Installed the `pfBlockerNG-devel` package for advanced network filtering.
* Generated and integrated a MaxMind GeoLite2 API key to download the global IP database.
* Configured the "Top Spammers" GeoIP list to target specific high-risk countries (Russia and China).
* Applied "Deny Both" firewall rules to the Inbound (WAN) and Outbound (LAN) interfaces.
* Verified the auto-generated block rules inside the pfSense firewall rules dashboard.

🔍 Phase 3: Endpoint Visibility & Active Response (Completed)

        Deployed the Wazuh Agent to the internal Windows 10 VM.

        Configured File Integrity Monitoring (FIM) to track unauthorized system changes.

        Enabled Vulnerability Detection to continuously scan the endpoint for unpatched software.

        Implemented Active Response scripts to automatically isolate threats upon detection.
