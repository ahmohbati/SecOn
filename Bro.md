Bro monitors your network traffic and creates logs:  
conn.log  
dns.log  
ftp.log  
http.log  
ssl.log  
notice.log  
and others  

We compile Bro with PF_RING so that you can spin up multiple Bro workers to handle more traffic.

For more information about Bro, please see:
https://www.bro.org/

* [Configure Bro to send email notifcation(s)](https://github.com/Security-Onion-Solutions/security-onion/wiki/Email#how-do-i-configure-bro-to-send-emails)

* [Send Bro logs to an external syslog collector](https://github.com/Security-Onion-Solutions/security-onion/wiki/ThirdPartyIntegration#how-do-i-send-bro-and-ossec-logs-to-an-external-syslog-collector)