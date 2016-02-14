#### Bro * n
`/opt/bro/etc/node.cfg`

We compile Bro with [PF_RING](https://github.com/Security-Onion-Solutions/security-onion/wiki/PF_RING) so that you can spin up multiple Bro workers to handle more traffic.

#### Custom Scripts
`/opt/bro/share/bro/site/local.bro`

* You can add custom scripts in `/opt/bro/share/bro/site/local.bro`. 
To check and see if the Bro script has fired a Notice, go to ELSA, click Notice, and then click "Top Notice Types".

#### Email
`/opt/bro/etc/broctl.cfg`

* To configure email notifications, please see:

https://github.com/Security-Onion-Solutions/security-onion/wiki/Email#how-do-i-configure-bro-to-send-emails

#### Logs
`/nsm/bro/logs`

Bro monitors your network traffic and creates logs, such as:  
##### conn.log
* TCP/UDP/ICMP connections

* For more information, see: https://www.bro.org/sphinx-git/scripts/base/protocols/conn/main.bro.html#type-Conn::Info

##### dns.log

* DNS activity	  

* For more information ,see: https://www.bro.org/sphinx-git/scripts/base/protocols/dns/main.bro.html#type-DNS::Info

##### ftp.log

* FTP activity

* For more information, see: https://www.bro.org/sphinx-git/scripts/base/protocols/ftp/info.bro.html#type-FTP::Info
	  
##### http.log

* HTTP requests and replies

* For more information, see: https://www.bro.org/sphinx-git/scripts/base/protocols/http/main.bro.html#type-HTTP::Info
	  
##### ssl.log

* SSL/TLS handshake info
	  
* For more information, see: https://www.bro.org/sphinx-git/scripts/base/protocols/ssl/main.bro.html#type-SSL::Info

##### notice.log

* Bro notices	  

* For more information, see: https://www.bro.org/sphinx-git/scripts/base/frameworks/notice/main.bro.html#type-Notice::Info

...and others, which can be researched here:  
https://www.bro.org/sphinx-git/script-reference/log-files.html

As you can see, Bro log data can provide a wealth of information to the analyst, all easily accessible through [ELSA](https://github.com/Security-Onion-Solutions/security-onion/wiki/ELSA). 

#### Syslog
`/etc/syslog-ng/syslog-ng.conf`

* To forward Bro logs to an external syslog collector, please see: 

https://github.com/Security-Onion-Solutions/security-onion/wiki/ThirdPartyIntegration#how-do-i-send-bro-and-ossec-logs-to-an-external-syslog-collector

For more information about Bro, please see:
https://www.bro.org/