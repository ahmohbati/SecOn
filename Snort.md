### Description
Snort is a Network Intrusion Detection System (NIDS).  It sniffs network traffic and generates IDS alerts.

### Performance
In Security Onion, we compile Snort with [PF_RING](PF_RING) to allow you to spin up multiple instances to handle more traffic.

### Configuration
You can configure Snort via snort.conf:  
`/etc/nsm/HOSTNAME-INTERFACE/snort.conf`  
(where HOSTNAME is your actual hostname and INTERFACE is your actual sniffing interface)

### Logging
If you need to troubleshoot Snort, check the Snort log file:  
`/var/log/nsm/HOSTNAME-INTERFACE/snortu-X.log`  
(where HOSTNAME is your actual hostname, INTERFACE is your actual sniffing interface, and X represents the number of PF_RING instances)

### More Information
For more information about Snort, please see:  
http://snort.org