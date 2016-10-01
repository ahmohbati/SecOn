#### Check services

- Verify services are running:  
```sudo service nsm status```

- If any services are not running, try starting them:  
```sudo service nsm start```

#### Tuning / Miscellaneous
- Check your sniffing interfaces to see if they have Receive Side Scaling (RSS) queues (if so, you may need to reduce to 1): https://redmine.openinfosecfoundation.org/projects/suricata/wiki/Packet_Capture

- Are you monitoring network traffic that has VLAN tags?  If so, take a look at our [VLAN](VLAN-Traffic) page.

- If you’re monitoring IP address ranges other than private RFC1918 address space (192.168.0.0/16, 10.0.0.0/8, 172.16.0.0/12), you should update your sensor configuration with the correct IP ranges. Sensor configuration files can be found in `/etc/nsm/$HOSTNAME-$INTERFACE/`. Modify either `snort.conf` or `suricata.yaml` (depending on which IDS engine you chose during `sosetup`) and update the `HOME_NET` variable.  (As of securityonion-setup - 20120912-0ubuntu0securityonion222, Setup should automatically ask you for HOME_NET and configure these for you.) You may also want to consider updating the `EXTERNAL_NET` variable.  If you're running prads (you're probably not), then update the `home_nets` variable in `prads.conf`. Then update Bro’s network configuration in `/opt/bro/etc/networks.cfg`.  Restart the sensor processes:<br>
`sudo nsm_sensor_ps-restart`

- If you have Internet access, create an IDS alert by typing the following at a terminal:<br>
`curl http://testmyids.com`

- As of securityonion-setup - 20120912-0ubuntu0securityonion201, Setup now defaults to only opening port 22 in the firewall.  If you need to connect OSSEC agents, syslog devices, or analyst VMs, you can run the new `so-allow` utility which will walk you through creating firewall rules to allow these devices to connect.  For more information, please see the [firewall](Firewall) page.<br>

- Full-time analysts should use an [Analyst VM](Analyst-VM).

- Login to Sguil and review your IDS alerts. Squert and ELSA can be accessed by visiting https://YourSecurityOnionBox/ (please note the HTTPS) for additional in-depth analysis.<br>

- Run the following to see how your sensor is coping with the load. You should check this on a daily basis to make sure your sensor is not dropping packets. Consider adding it to a cronjob and having it emailed to you (see the “configure email” link below).<br>
`sudo sostat | less`

- Any IDS/NSM system needs to be tuned for the network it’s monitoring. Please see [ManagingAlerts](ManagingAlerts). You should only run the signatures you really care about.<br>

- Review and categorize events every day with the goal being to categorize all events every day. Neglecting to do so will result in database/Sguil issues as the number of uncategorized events continues to increase on a daily basis.<br>

- On the server running the Sguil database, set the `DAYSTOKEEP` variable in `/etc/nsm/securityonion.conf` to however many days you want to keep in your archive. The default is 30, but you may need to adjust it based on your organization’s detection/response policy and your available disk space.<br>

- Modern versions of Setup automatically disable http_agent if you choose "Best Practices".  However, if you chose Custom and then chose to enable [http_agent](http_agent), you should tune it using http_agent.conf.  If you're running ELSA, you already have all the Bro HTTP logs available there, so you might want to avoid duplicating those logs in the Sguil database by disabling http_agent as follows.<br>
`sudo nsm_sensor_ps-stop --only-http-agent`  
`sudo sed -i 's|HTTP_AGENT_ENABLED="yes"|HTTP_AGENT_ENABLED="no"|g' /etc/nsm/*/sensor.conf`

- [Disable any unneeded sensor processes](DisablingProcesses)<br>

- Tune the number of PF_RING instances for Snort/Suricata and Bro: [PF_RING](PF_RING)

#### Optional

- *Optional:* exclude unnecessary traffic from your monitoring using [BPF](BPF).<br>

- *Optional:* add new Sguil user accounts with the following:<br>
`sudo nsm_server_user-add`

- *Optional*, but highly recommended: configure [Email](email) for alerting and reporting.<br>

- *Optional:* place `/etc` under version control.  If your organization doesn't already have a standard version control tool, you can use [bazaar](https://help.ubuntu.com/12.04/serverguide/bazaar.html), [git](http://git-scm.com/), <a href='https://help.ubuntu.com/12.04/serverguide/etckeeper.html'>etckeeper</a>:<br>
`sudo apt-get install etckeeper`

- *Optional:* need “remote desktop” access to your Security Onion sensor or server? We recommend SSH X-Forwarding as shown above, but if you want something more rdp-like, you can install [FreeNX](https://github.com/Security-Onion-Solutions/security-onion/wiki/FreeNX) or <a href='http://www.xrdp.org/'>xrdp</a> (please note we do NOT support either of these):  
`sudo apt-get install xrdp`  

#### Learn More

- Read more about the tools contained in Security Onion: [Tools](Tools)