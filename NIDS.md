### Description
NIDS stands for Network Intrusion Detection System.  It is a means of monitoring network traffic, looking for specific activity, and generating alerts.

### Usage
Security Onion can run either [Snort](Snort) or [Suricata](Suricata) as its Network Intrusion Detection System (NIDS).  When you run Setup and choose Evaluation Mode, it will automatically default to Snort.  If you choose Production Mode, you will be asked to choose whether you want to run [Snort](Snort) or [Suricata](Suricata).

### Performance
In Security Onion, we compile both of these with [PF_RING](PF_RING) for higher performance.

### Analysis
You can analyze NIDS alerts from Snort/Suricata via:
- [Squert](Squert)
- [ELSA](ELSA)
- [Sguil](Sguil)

### More Information
For more information about Snort, please see:  
https://github.com/Security-Onion-Solutions/security-onion/wiki/Snort

For more information about Suricata, please see:  
https://github.com/Security-Onion-Solutions/security-onion/wiki/Suricata