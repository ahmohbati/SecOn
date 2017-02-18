We compile Snort with [PF_RING](PF_RING) to allow you to spin up multiple instances to handle more traffic.

Configuration:  
/etc/nsm/HOSTNAME-INTERFACE/snort.conf  
(where HOSTNAME is your actual hostname and INTERFACE is your actual sniffing interface)

Log file:  
/var/log/nsm/HOSTNAME-INTERFACE/snortu-X.log  
(where HOSTNAME is your actual hostname, INTERFACE is your actual sniffing interface, and X represents the number of PF_RING instances)

For more information about Snort, please see:
http://snort.org