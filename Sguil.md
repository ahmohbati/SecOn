* Developed by Bamm Visscher:  
http://sguil.net

* tcl/tk (not web-based)

* Single central MySQL database

* For login information, please see:  
https://github.com/Security-Onion-Solutions/security-onion/wiki/Passwords#sguil

* Data types:

  * NIDS alerts from Snort/Suricata (if snort_agent is enabled)
  * HIDS alerts from OSSEC (if ossec_agent is enabled)
  * session data from PRADS (if PRADS and sancp_agent are enabled)
  * asset data from PRADS (if PRADS and pads_agent are enabled)
  * HTTP logs from Bro (if http_agent is enabled)

* Can pivot to transcript/Wireshark/NetworkMiner by right-clicking the Alert ID field.

- Pivot to ELSA by right-clicking an IP address and choosing "ELSA IP Lookup".

* You can change fonts by clicking File --> Change Font.

* You can resize columns by right-clicking on the column heading.

* [Create an Autocat rule to automatically classify events](https://github.com/Security-Onion-Solutions/security-onion/wiki/ManagingAlerts#autocategorize-events).

* [Configure Sguil alert email notification(s)](https://github.com/Security-Onion-Solutions/security-onion/wiki/Email#how-do-i-configure-sguil-to-send-alerts-via-email)

* [Configure retention for Sguil alerts](https://github.com/Security-Onion-Solutions/security-onion/wiki/ManagingAlerts#sguil-days-to-keep)
