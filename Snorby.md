* Snorby is now considered un-maintained and is no longer included in Security Onion as of Security Onion 14.04.  If you are currently using Snorby in your 12.04 installation, you should go ahead and begin transitioning to [Squert](Squert), [Sguil](Sguil), and/or [ELSA](ELSA).  To disable Snorby in your existing deployment, please see:  
https://github.com/Security-Onion-Solutions/security-onion/wiki/DisablingProcesses#disabling-snorby

* Originally developed by Dustin Webber:  
https://github.com/snorby/snorby

* Web 2.0, Ajax, Ruby-on-Rails

* Log into Snorby using the EMAIL ADDRESS and password you specified in Setup

* Snorby has its own MySQL database (separate from the Sguil and ELSA databases)

* The Snorby database only stores NIDS alerts from Snort or Suricata

* Pivot from a NIDS alert in Snorby to CapME to access full packet capture:  
https://github.com/Security-Onion-Solutions/security-onion/wiki/CapMeAuthentication

* Pivot from an IP address in Snorby to ELSA for related logs (Bro logs, OSSEC logs, syslog)

* If you need to wipe the Snorby database, please see:  
https://github.com/Security-Onion-Solutions/security-onion/wiki/WipingSnorby

* Be aware that Snorby uses highcharts. Read the <a href='http://shop.highsoft.com/highcharts.html'>highcharts</a> <a href='http://shop.highsoft.com/faq/non-commercial#what-is-non-commercial'>license</a> to determine if you need to purchase a commercial license.  If you feel that you would be required to purchase a commercial license but are unwilling/unable to, you can [disable/remove Snorby altogether](DisablingProcesses#disabling-snorby) or de-activate HighCharts (the charts on the bottom half of the Snorby Dashboard will be blank, but nothing else in Snorby should be affected):<br>
<pre><code>sudo mv /opt/snorby/public/javascripts/highcharts.js /opt/snorby/public/javascripts/highcharts.js.DISABLED<br>
</code></pre>

* ####How do I change the timezone in Snorby?####
** click Settings in the upper right corner
** click the drop-down box next to "Time zone"
** select your time zone from the list
** click the "Update Settings" button
** set the same timezone in CapMe's timezone.php:<br>
<a href='http://blog.securityonion.net/2014/01/new-capme-package-allows-you-to.html'>http://blog.securityonion.net/2014/01/new-capme-package-allows-you-to.html</a>