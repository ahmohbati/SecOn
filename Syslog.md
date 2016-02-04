Security Onion uses syslog-ng as its syslog collector.

For more information, please see:  
https://syslog-ng.org/

* Configuration file located at `/etc/syslog-ng/syslog-ng.conf`
* Security Onion currently uses syslog-ng to forward Bro, IDS, and OSSEC logs to ELSA.
* Syslog-ng can be integrated with [third-party systems](https://github.com/Security-Onion-Solutions/security-onion/wiki/ThirdPartyIntegration) to forward Bro, OSSEC, or IDS alerts.