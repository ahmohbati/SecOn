Security Onion uses OSSEC as a Host Intrusion Detection System.  OSSEC is monitoring and defending Security Onion itself and you can add OSSEC agents to monitor other hosts on your network as well.

For more information about OSSEC, please see:  
http://ossec.net

#### Adding an Agent ####
If you wish to install an OSSEC agent on other hosts on your network, ensure the agent is installed on the host(s) to be monitored, then perform the steps defined here:

http://ossec-docs.readthedocs.org/en/latest/manual/agent/agent-management.html#managing-agents

Additionally, you may want to:

* [Configure OSSEC to send email notification(s)](https://github.com/Security-Onion-Solutions/security-onion/wiki/Email#how-do-i-configure-ossec-to-send-emails)

* [Send OSSEC logs to an external syslog collector ](https://github.com/Security-Onion-Solutions/security-onion/wiki/ThirdPartyIntegration#how-do-i-send-bro-and-ossec-logs-to-an-external-syslog-collector)