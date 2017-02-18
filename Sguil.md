### What is Sguil?
From http://sguil.net:
> Sguil (pronounced sgweel) is built by network security analysts for network security analysts. Sguil's main component is an intuitive GUI that provides access to realtime events, session data, and raw packet captures. Sguil facilitates the practice of Network Security Monitoring and event driven analysis.

* Developed by Bamm Visscher:  
http://sguil.net  
http://nsmwiki.org/Sguil  
http://nsmwiki.org/Sguil_Client  

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

* resize columns by right-clicking on the column heading

* pivot to transcript/Wireshark/NetworkMiner by right-clicking the Alert ID

* automatically pivot to ASCII transcript by middle-clicking the Alert ID

* pivot to ELSA by right-clicking an IP address and choosing "ELSA IP Lookup".

* change fonts by clicking File --> Change Font.

* Sguil client settings are stored in `/etc/sguil/sguil.conf`:
  * You can enable "Show Rule", "Show Packet Data", and "Display Detail" (respectively) by setting the following (also see https://groups.google.com/d/topic/security-onion/MJaAlxgpMvU/discussion):
  ```
set SHOWRULE 1
set PACKETINFO 1
set DISPLAY_GENERIC 1
  ```
  * You can separate realtime alerts into separate panes, based on severity level, by editing `/etc/sguil/sguil.conf` as follows:

  ```
    #Number of RealTime Event Panes    
    #set RTPANES 1    
    set RTPANES 3    
 
    # Specify which priority events go into what pane   
    # According to the latest classification.config from snort,   
    # there are only 4 priorities. The sguil spp_portscan mod   
    # uses a priority of 5.    
    #set RTPANE_PRIORITY(0) "1 2 3 4 5"  
    set RTPANE_PRIORITY(0) "1"  
    set RTPANE_PRIORITY(1) "2 3"  
    set RTPANE_PRIORITY(2) "4 5"   
  ```
* It is important to ensure events displayed in Sguil are regularly classified, or else it could cause problems with the Sguil database. Consider creating an [autocat rule](https://github.com/Security-Onion-Solutions/security-onion/wiki/ManagingAlerts#autocategorize-events) to assist with this.

* [Configure Sguil alert email notification(s)](https://github.com/Security-Onion-Solutions/security-onion/wiki/Email#how-do-i-configure-sguil-to-send-alerts-via-email)

* [Configure retention for Sguil alerts](https://github.com/Security-Onion-Solutions/security-onion/wiki/ManagingAlerts#sguil-days-to-keep)