### Description
From https://github.com/mcholste/elsa:
> Enterprise Log Search and Archive (ELSA) is a three-tier log receiver, archiver, indexer, and web frontend for incoming syslog. It leverages syslog-ng's pattern-db parser for efficient log normalization and Sphinx full-text indexing for log searching. 

* Developed by Martin Holste:  
https://github.com/mcholste/elsa  
https://github.com/mcholste/elsa/wiki/Documentation

* Web interface for hunting through logs ([Bro](Bro), [NIDS alerts](NIDS), [OSSEC](OSSEC), [syslog](syslog))

* Works best with Chromium/Chrome browser

* More data types than all other interfaces

* In Security Onion 14.04, ELSA has dynamic bar charts and dashboards.

* The ELSA web interface authenticates against the Sguil user database, so you should be able to login to ELSA using the same username/password you use to login to Sguil/Squert

* By default, ELSA searches the last 2 days worth of logs.  You can control this using the From and To fields.

* Can pivot to [CapME](CapMe) to access full packet capture.  For any log relating to TCP traffic that has timestamp; src ip; source port; destination ip; and destination port, you can click Info, Plugin, getPcap to pivot to CapMe.  Enter your username and password and CapMe will retrieve the pcap and render it as an ASCII transcript.  If ELSA doesn't show the getPcap plugin, then the log you were trying to pivot from didn't contain all of the fields listed above that are necessary to active the getPcap plugin.

* Very fast, very scalable (each sensor has its own mysql database and sphinx index)

* When you query the ELSA web interface, it queries all ELSA databases in parallel and then gives you the aggregate results

* You can use the command-line version of ELSA as follows (replacing example.com with your desired search criteria):
  ````
sh /opt/elsa/contrib/securityonion/contrib/cli.sh "example.com" 
  ````
The output is in JSON, so you might want to pipe the results into `jq`:
  ````
sh /opt/elsa/contrib/securityonion/contrib/cli.sh "example.com" | jq '.'
  ````
* Large number of Perl processes?<br>
See: [Why does sostat show high load/CPU usage and large number of Perl processes?](https://github.com/Security-Onion-Solutions/security-onion/wiki/FAQ#why-does-sostat-show-high-loadcpu-usage-and-large-number-of-perl-processes) 

* Problems with ELSA buffers?<br>
See: 
[Why does sostat show a high number of ELSA buffers in queue?](https://github.com/Security-Onion-Solutions/security-onion/wiki/FAQ#why-does-sostat-show-a-high-number-of-elsa-buffers-in-queue)

* For more information, please see:  
[ELSA Query Tips](ELSAQueryTips)  
[Custom ELSA Parsers](CustomELSAParsers)

* ELSA tuning:

  https://github.com/mcholste/elsa/wiki/Documentation#Lowvolumeconfigurationtuning

  https://groups.google.com/forum/#!searchin/enterprise-log-search-and-archive/%22allowed_temp_percent%22/enterprise-log-search-and-archive/auUSYj77ctw/mzF-YqVa5KMJ

  https://groups.google.com/d/topic/security-onion/xLxTGQs30ho/discussion

  https://groups.google.com/d/topic/enterprise-log-search-and-archive/Z-6YrCD_FkU/discussion