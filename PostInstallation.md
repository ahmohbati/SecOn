Verify services are running:  
```sudo service nsm status```

If any services are not running, try starting them:  
```sudo service nsm start```

#### Tuning / Miscellaneous
- Are you monitoring network traffic that has VLAN tags?  If so, take a look at our [VLAN](VLAN-Traffic) page.
<li>If you’re monitoring IP address ranges other than private RFC1918 address space (192.168.0.0/16, 10.0.0.0/8, 172.16.0.0/12), you should update your sensor configuration with the correct IP ranges. Sensor configuration files can be found in `/etc/nsm/$HOSTNAME-$INTERFACE/`. Modify either `snort.conf` or `suricata.yaml` (depending on which IDS engine you chose during `sosetup`) and update the `HOME_NET` variable. Also update the `home_nets` variable in `prads.conf`. Then update Bro’s network configuration in `/opt/bro/etc/networks.cfg`.  Restart the sensor processes:<br>
<pre><code>sudo nsm_sensor_ps-restart<br>
</code></pre>
<ol></li>
<li>If you have Internet access, create an IDS alert by typing the following at a terminal:<br>
<pre><code>curl http://testmyids.com<br>
</code></pre>
</li><li>As of securityonion-setup - 20120912-0ubuntu0securityonion201, Setup now defaults to only opening port 22 in the firewall.  If you need to connect OSSEC agents, syslog devices, or analyst VMs, you can run the new `so-allow` utility which will walk you through creating firewall rules to allow these devices to connect.  For more information, please see the [firewall](Firewall) page.<br>
</li><li>Full-time analysts should install Security Onion in a VM on their workstation (run through the Ubuntu installer, but do not run our Setup wizard). This gives you a local copy of Wireshark, NetworkMiner, and our customized Sguil client.  Launch the Sguil client and connect to the IP/hostname of your production Sguil sensor (you may need to run so-allow as described in the previous step).  This allows you to investigate pcaps without fear of impacting your production server/sensors. To change the resolution of your Security Onion VM, install the Virtual Tools for your virtualization solution or use xrandr. For a list of available screen resolutions, simply execute “xrandr”. To set the screen resolution (replace W and H with the actual Width and Height desired):<br>
<pre><code>xrandr -s WxH<br>
</code></pre>
</li><li>Login to Sguil and review your IDS alerts. Squert and ELSA can be accessed by visiting <a href='https://server/'>https://server/</a> for additional in-depth analysis.<br>
</li><li>Run the following to see how your sensor is coping with the load. You should check this on a daily basis to make sure your sensor is not dropping packets. Consider adding it to a cronjob and having it emailed to you (see the “configure email” link below).<br>
<pre><code>sudo sostat | less<br>
</code></pre>
</li><li>Please note that any IDS/NSM system needs to be tuned for the network it’s monitoring. Please see [ManagingAlerts](ManagingAlerts). You should only run the signatures you really care about.<br>
</li><li>Also note that you should be looking at and categorizing events every day with the goal being to categorize all events every day. Even if you don’t use the Sguil console for your primary analysis, you need to log into it periodically and F8 old events to keep the real time queue from getting too big. Neglecting to do so will result in database/Sguil issues as the number of uncategorized events continues to increase on a daily basis. Please see the <a href='http://nsmwiki.org/Sguil_Client'>Sguil client page on NSMwiki</a>.<br>
</li><li>On the server running the Sguil database, set the `DAYSTOKEEP` variable in `/etc/nsm/securityonion.conf` to however many days you want to keep in your archive. The default is 365, but you may need to adjust it based on your organization’s detection/response policy and your available disk space.<br>
</li><li>You should also tune [http_agent](http_agent).  If you're running ELSA, you already have all the Bro HTTP logs available there, so you might want to disable http_agent to avoid duplicating those logs in the Sguil database:<br>
<pre><code># Terminate the running http_agent<br>
sudo nsm_sensor_ps-stop --only-http-agent<br>
# Disable http_agent<br>
sudo sed -i 's|HTTP_AGENT_ENABLED="yes"|HTTP_AGENT_ENABLED="no"|g' /etc/nsm/*/sensor.conf<br>
</code></pre>
</li><li>[Disable any unneeded sensor processes](DisablingProcesses)<br>
</li><li>Tune the number of PF_RING instances for Snort/Suricata and Bro: [PF_RING](PF_RING)
</li><li>*Optional:* exclude unnecessary traffic from your monitoring using [BPF](BPF).<br>
</li><li>*Optional:* add new Sguil user accounts with the following:<br>
<pre><code>sudo nsm_server_user-add<br>
</code></pre>
</li><li>*Optional*, but highly recommended: configure [Email](email) for alerting and reporting.<br>
</li><li>*Optional*, but highly recommended: place `/etc` under version control.  If your organization doesn't already have a standard version control tool, you can use [bazaar](https://help.ubuntu.com/12.04/serverguide/bazaar.html), [git](http://git-scm.com/), <a href='https://help.ubuntu.com/12.04/serverguide/etckeeper.html'>etckeeper</a>:<br>
<pre><code>sudo apt-get install etckeeper<br>
</code></pre>
</li><li>*Optional:* need “remote desktop” access to your Security Onion sensor or server? We recommend SSH X-Forwarding as shown above, but if you want something more rdp-like, you can install [FreeNX](https://github.com/Security-Onion-Solutions/security-onion/wiki/FreeNX) or <a href='http://www.xrdp.org/'>xrdp</a>:
```
sudo apt-get install xrdp
```
Please note that we do not support FreeNX or xrdp.<br>
</li><li>Read more about the tools contained in Security Onion: [Tools](Tools)