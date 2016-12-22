* Originally developed by Paul Halliday:  
http://www.squertproject.org/

* Security Onion maintains its own fork of Squert:  
http://blog.securityonion.net/2016/09/squert-development.html

* PHP web interface to Sguil database

* Works best with Chromium/Chrome browser

* Squert authenticates against the Sguil user database, so you should be able to login to Squert using the same username/password you use to login to Sguil

* Gives you access to the following data types:
  * NIDS alerts
  * HIDS alerts
  * Asset data from PRADS (if PRADS and pads_agent are enabled)
  * HTTP logs from Bro (if http_agent is enabled)

* The default view shows alerts from today.  To show older alerts, click "INTERVAL", then click the 2 right arrows, set your custom date, and click Squert's refresh button (two circular arrows).

* Can pivot to CapMe for full packet capture.  To do this, drill into an event and click on the Event ID.

* Can pivot to ELSA to query Bro logs.  To do this, click an IP address, port, or signature, and then click ELSA.  In Security Onion 14.04, Squert pivots to ELSA using a relative hyperlink, so it should use the same hostname or IP address that you used to connect to Squert.  If you're still using Security Onion 12.04 and you need to change the IP address that Squert uses to pivot to ELSA, you can use the following code copied from sosetup (replacing $IP with your actual IP address or hostname):
```
# Pivot from Squert to ELSA
URL="https://$IP:3154/?query_string=\"\${var}\"%20groupby:program"
HEXVAL=$(xxd -pu -c 256 <<< "$URL")
sudo mysql --defaults-file=/etc/mysql/debian.cnf -Dsecurityonion_db -e "INSERT IGNORE INTO filters (type,username,global,name,notes,alias,filter) VALUES ('url','','1','454C5341','','ELSA','$HEXVAL');"
```