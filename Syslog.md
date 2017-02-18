Security Onion uses syslog-ng as its primary syslog collector.

* Configuration file is located at `/etc/syslog-ng/syslog-ng.conf`
* Security Onion uses syslog-ng to forward Bro, IDS, and OSSEC logs to ELSA.
* Syslog-ng can be integrated with [third-party systems](https://github.com/Security-Onion-Solutions/security-onion/wiki/ThirdPartyIntegration) to forward Bro, OSSEC, or IDS alerts.

For more information about syslog-ng, please see:  
https://syslog-ng.org/

syslog-ng listens on port 514 (TCP and UDP) for incoming syslog from other devices (you may need to run [so-allow](firewall) to allow traffic from the IP address of your syslog sender).  This gives you basic log collection.  If you'd like those logs collected from other devices to be analyzed, another option is to configure OSSEC to receive syslog directly on a port other than the syslog-ng port of 514:  
http://ossec-docs.readthedocs.org/en/latest/syntax/head_ossec_config.remote.html  
http://www.ossec.net/ossec-docs/OSSEC-book-ch3.pdf