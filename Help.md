# Having problems?  Try the suggestions below. #

  * Are you running the [latest version of Security Onion](Upgrade)?
  * Check the [FAQ](FAQ).
  * Search the [Security Onion Mailing Lists](MailingLists).
  * Search the documentation and mailing lists of the tools contained within Security Onion: [Tools](Tools)
  * Run "sostat" for some diagnostics:
```
sudo sostat | less
```
  * If any of the NSM processes show up as failed, try restarting them:
```
sudo service nsm restart
```
  * Check log files in /var/log/nsm/ for any errors or possible clues.
  * If this is a sensor sending alerts to master server, is autossh running?
```
pgrep -lf autossh
```
  * If you're having problems with Snorby, check the log files in /opt/snorby/log/ and /var/log/apache2/ and see if its processes are running:
```
pgrep -lf delayed_job
```
  * Are you able to duplicate the problem on a fresh Security Onion installation?
  * Check the [Roadmap](Roadmap) to see if this is a known issue that we are working on.
  * If all else fails, please send an email to our [security-onion mailing list](MailingLists).
  * Need training or commercial support?  http://www.securityonionsolutions.com