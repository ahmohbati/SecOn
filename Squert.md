### Description
From http://www.squertproject.org/:
> Squert is a web application that is used to query and view event data stored in a Sguil database (typically IDS alert data). Squert is a visual tool that attempts to provide additional context to events through the use of metadata, time series representations and weighted and logically grouped result sets. The hope is that these views will prompt questions that otherwise may not have been asked. 

Squert was originally developed by Paul Halliday:  
http://www.squertproject.org/

Security Onion maintains its own fork of Squert:  
http://blog.securityonion.net/2016/09/squert-development.html

Squert is a PHP web interface to the [Sguil](Sguil) database and works best with Chromium/Chrome browsers.

### Authentication
Squert authenticates against the Sguil user database, so you should be able to login to Squert using the same username/password you use to login to Sguil.

### Data Types
Squert gives you access to the following data types:
  * [NIDS](NIDS) alerts
  * [HIDS](OSSEC) alerts
  * Asset data from PRADS (if PRADS and pads_agent are enabled)
  * HTTP logs from Bro (if http_agent is enabled)

* The default view shows alerts from today.  To show older alerts, click "INTERVAL", then click the 2 right arrows, set your custom date, and click Squert's refresh button (two circular arrows).

### Pivoting to Full Packet Capture
Squert can pivot to [CapMe](CapMe) for full packet capture.  To do this, drill into an event and click on the Event ID.

### Pivoting to ELSA
Squert can pivot to [ELSA](ELSA) to query Bro logs, OSSEC logs, syslog, etc.  To do this, click an IP address, port, or signature, and then click ELSA.  In Security Onion 14.04, Squert pivots to ELSA using a relative hyperlink, so it should use the same hostname or IP address that you used to connect to Squert.  If you're still using Security Onion 12.04 and you need to change the IP address that Squert uses to pivot to ELSA, you can use the following code copied from sosetup (replacing $IP with your actual IP address or hostname):
```
# Pivot from Squert to ELSA
URL="https://$IP:3154/?query_string=\"\${var}\"%20groupby:program"
HEXVAL=$(xxd -pu -c 256 <<< "$URL")
sudo mysql --defaults-file=/etc/mysql/debian.cnf -Dsecurityonion_db -e "INSERT IGNORE INTO filters (type,username,global,name,notes,alias,filter) VALUES ('url','','1','454C5341','','ELSA','$HEXVAL');"
```

### Adding your own pivots
If you're running the latest version of Squert, you can also add your own pivots as follows:
* In the upper right corner of Squert, click the Filters button.
* Set the type to URL.
* Click the + button.
* Click your New entry.
* Fill out the alias, name, notes, and URL fields as applicable.
* Click the Update button.
* Close the Filters and URLs window.
* To test, drill into an event and click an IP address.  A context menu will appear and display your new link.  Click the new link and verify that it opens a new browser tab going to the site you specified and passing the IP address that you clicked on.
