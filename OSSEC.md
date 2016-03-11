Security Onion uses OSSEC as a Host Intrusion Detection System (HIDS).  OSSEC is monitoring and defending Security Onion itself and you can add OSSEC agents to monitor other hosts on your network as well.

Additionally, you may want to:

* [Configure OSSEC to send email notification(s)](https://github.com/Security-Onion-Solutions/security-onion/wiki/Email#how-do-i-configure-ossec-to-send-emails)

* [Send OSSEC logs to an external syslog collector ](https://github.com/Security-Onion-Solutions/security-onion/wiki/ThirdPartyIntegration#how-do-i-send-bro-and-ossec-logs-to-an-external-syslog-collector)

For more information about OSSEC, please see:  
http://ossec.net

#### Active Response ###
Sometimes, OSSEC may recognize legitimate activity as potentially malicious, and engage in Active Response to block a connection.  This may result in unintended consequences and/or blacklisting of trusted IPs. 
You can whitelist your IP address and change other settings in `/var/ossec/etc/ossec.conf` to prevent 
this from occurring:<br/>

`<global>`<br/>
`<white_list>desired_ip</white_list>`<br/>
`</global>`

#### Adding Agents ####

The OSSEC agent is cross platform and you can download agents for Windows/Unix/Linux/FreeBSD from the OSSEC website.  Once you've installed the OSSEC agent on the host(s) to be monitored, then perform the steps defined here:

http://ossec-docs.readthedocs.org/en/latest/manual/agent/agent-management.html#managing-agents

#### Automated Deployment ####

Many individuals require or prefer the ability to automatically deploy OSSEC agents on endpoint machines.  Although **this is currently untested and unsupported**, Auto-OSSEC provides a method for achieving this goal.

For more information, please see:
https://github.com/binarydefense/auto-ossec