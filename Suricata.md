### Description
From https://suricata-ids.org:
> Suricata is a free and open source, mature, fast and robust network threat detection engine.  Suricata inspects the network traffic using a powerful and extensive rules and signature language, and has powerful Lua scripting support for detection of complex threats.

### Performance
We compile Suricata with [PF_RING](PF_RING) to allow you to spin up multiple workers to handle more traffic.

### Configuration
/etc/nsm/HOSTNAME-INTERFACE/suricata.yaml  
(where HOSTNAME is your actual hostname and INTERFACE is your actual sniffing interface)

### Log File
/var/log/nsm/HOSTNAME-INTERFACE/suricata.log  
(where HOSTNAME is your actual hostname and INTERFACE is your actual sniffing interface)

### More Information
For more information about Suricata, please see:  
https://suricata-ids.org/