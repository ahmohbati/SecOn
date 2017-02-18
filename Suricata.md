We compile Suricata with [PF_RING](PF_RING) to allow you to spin up multiple workers to handle more traffic.

Configuration:  
/etc/nsm/HOSTNAME-INTERFACE/suricata.yaml  
(where HOSTNAME is your actual hostname and INTERFACE is your actual sniffing interface)

Log file:  
/var/log/nsm/HOSTNAME-INTERFACE/suricata.log  
(where HOSTNAME is your actual hostname and INTERFACE is your actual sniffing interface)

For more information about Suricata, please see:  
https://suricata-ids.org/