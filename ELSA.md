* Developed by Martin Holste:  
https://code.google.com/p/enterprise-log-search-and-archive/

* Web interface for hunting through logs (Bro, Snort, OSSEC, syslog)

* More data types than all other interfaces

* Can pivot to CapME to access full packet capture:  
[CapME Authentication](CapMeAuthentication)

* Very fast, very scalable (each sensor has its own mysql database and sphinx index)

* The ELSA web interface authenticates against the Sguil user database, so you should be able to login to ELSA using the same username/password you use to login to Sguil

* For more information, please see:  
[ELSA Query Tips](ELSAQueryTips)  
[Custom ELSA Parsers](CustomELSAParsers)

* ELSA tuning:

https://code.google.com/p/enterprise-log-search-and-archive/wiki/Documentation#Low_volume_configuration_tuning

https://groups.google.com/forum/#!searchin/enterprise-log-search-and-archive/%22allowed_temp_percent%22/enterprise-log-search-and-archive/auUSYj77ctw/mzF-YqVa5KMJ

https://groups.google.com/d/topic/security-onion/xLxTGQs30ho/discussion

https://groups.google.com/d/topic/enterprise-log-search-and-archive/Z-6YrCD_FkU/discussion



