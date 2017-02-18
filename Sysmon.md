From https://technet.microsoft.com/en-us/sysinternals/sysmon:
> System Monitor (Sysmon) is a Windows system service and device driver that, once installed on a system, remains resident across system reboots to monitor and log system activity to the Windows event log. It provides detailed information about process creations, network connections, and changes to file creation time. By collecting the events it generates using Windows Event Collection or SIEM agents and subsequently analyzing them, you can identify malicious or anomalous activity and understand how intruders and malware operate on your network.

Josh Brower did some great work integrating sysmon into Security Onion:  
https://digital-forensics.sans.org/community/papers/gcfa/sysmon-enrich-security-onions-host-level-capabilities_10612

SwiftOnSecurity has a great sysmon config file to use as a starting point:  
https://github.com/SwiftOnSecurity/sysmon-config

You may also want to read this article for additional explanation:  
https://medium.com/@lennartkoopmann/explaining-and-adapting-tays-sysmon-configuration-27d9719a89a8#.bgzhylmn8