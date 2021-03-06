Previously, when a user ran Setup and enabled ELSA, they would be able to log into ELSA and view OSSEC **archive** logs (the raw logs received by OSSEC) but they wouldn't be able to view OSSEC **alerts** (created based on OSSEC's analysis of the incoming logs as configured by the OSSEC ruleset).  I've pushed a new Setup package that will configure OSSEC to send alerts to local syslog if the user enables ELSA.

If you've already run Setup and would like to configure OSSEC to send alerts to ELSA, you can manually run the following commands:
```
sudo sed -i 's|  <rules>|  <syslog_output>\
      <server>127.0.0.1</server>\
  </syslog_output>\
\
  <rules>|g' /var/ossec/etc/ossec.conf

sudo /var/ossec/bin/ossec-control enable client-syslog

sudo service ossec-hids-server restart
```