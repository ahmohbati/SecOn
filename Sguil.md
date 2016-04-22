* Developed by Bamm Visscher:  
http://sguil.net

* pronounced like "squeal"

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

* You can pivot to transcript/Wireshark/NetworkMiner by right-clicking the Alert ID field.

* You can pivot to ELSA by right-clicking an IP address and choosing "ELSA IP Lookup".

* You can change fonts by clicking File --> Change Font.

* You can resize columns by right-clicking on the column heading.

* You can separate realtime alerts into separate panes, based on severity level, by editing `/etc/sguil/sguil.conf` as follows:

<pre><code>
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
</code></pre>
* It is important to ensure events displayed in Sguil are regularly classified, or else it could cause problems with the Sguil database. Consider creating an [autocat rule](https://github.com/Security-Onion-Solutions/security-onion/wiki/ManagingAlerts#autocategorize-events) to assist with this.

* [Configure Sguil alert email notification(s)](https://github.com/Security-Onion-Solutions/security-onion/wiki/Email#how-do-i-configure-sguil-to-send-alerts-via-email)

* [Configure retention for Sguil alerts](https://github.com/Security-Onion-Solutions/security-onion/wiki/ManagingAlerts#sguil-days-to-keep)