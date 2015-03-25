# Tuning / Miscellaneous #
<li>If you’re monitoring IP address ranges other than private RFC1918 address space (192.168.0.0/16, 10.0.0.0/8, 172.16.0.0/12), you should update your sensor configuration with the correct IP ranges. Sensor configuration files can be found in /etc/nsm/HOSTNAME-INTERFACE/. Modify either snort.conf or suricata.yaml (depending on which IDS engine you chose during sosetup) and update the HOME\_NET variable. Also update the home\_nets variable in prads.conf. Then update Bro’s network configuration in /opt/bro/etc/networks.cfg.  Restart the sensor processes:<br>
<pre><code>sudo nsm_sensor_ps-restart<br>
</code></pre>
<ol></li>
<li>If you have Internet access, create an IDS alert by typing the following at a terminal:<br>
<pre><code>curl http://testmyids.com<br>
</code></pre>
</li><li>Full-time analysts should install Security Onion in a VM on their workstation (run through the Ubuntu installer, but do not run our Setup wizard). This gives you a local copy of Wireshark, NetworkMiner, and our customized Sguil client.  Launch the Sguil client and connect to the IP/hostname of your production Sguil sensor. This allows you to investigate pcaps without fear of impacting your production server/sensors. If you're using ELSA, you may want to install the Google Chrome browser (in addition to the already included Chromium) since it includes Flash needed to display the inline Flash charts.  To change the resolution of your Security Onion VM, install the Virtual Tools for your virtualization solution or use xrandr. For a list of available screen resolutions, simply execute “xrandr”. To set the screen resolution (replace W and H with the actual Width and Height desired):<br>
<pre><code>xrandr -s WxH<br>
</code></pre>
</li><li>Login to Sguil and review your IDS alerts. Squert, Snorby and ELSA can be accessed by visiting <a href='https://server/'>https://server/</a> for additional in-depth analysis.<br>
</li><li>Be aware that Snorby uses highcharts. Read the <a href='http://shop.highsoft.com/highcharts.html'>highcharts</a> <a href='http://shop.highsoft.com/faq/non-commercial#what-is-non-commercial'>license</a> to determine if you need to purchase a commercial license.  If you feel that you would be required to purchase a commercial license but are unwilling/unable to, you can <a href='http://code.google.com/p/security-onion/wiki/FAQ#How_do_I_disable_Snorby?'>disable/remove Snorby altogether</a> or de-activate HighCharts (the charts on the bottom half of the Snorby Dashboard will be blank, but nothing else in Snorby should be affected):<br>
<pre><code>sudo mv /opt/snorby/public/javascripts/highcharts.js /opt/snorby/public/javascripts/highcharts.js.DISABLED<br>
</code></pre>
</li><li>Harden your server and sensors by disabling any unneeded services and <a href='http://code.google.com/p/security-onion/wiki/Firewall'>firewalling</a> off any unused ports.<br>
</li><li>Run the following to see how your sensor is coping with the load. You should check this on a daily basis to make sure your sensor is not dropping packets. Consider adding it to a cronjob and having it emailed to you (see the “configure email” link below).<br>
<pre><code>sudo sostat | less<br>
</code></pre>
</li><li>Please note that any IDS/NSM system needs to be tuned for the network it’s monitoring. Please see <a href='http://code.google.com/p/security-onion/wiki/ManagingAlerts'>ManagingAlerts</a>. You should only run the signatures you really care about.<br>
</li><li>Also note that you should be looking at and categorizing events every day with the goal being to categorize all events every day. Even if you don’t use the Sguil console for your primary analysis, you need to log into it periodically and F8 old events to keep the real time queue from getting too big. Neglecting to do so will result in database/Sguil issues as the number of uncategorized events continues to increase on a daily basis. Please see the <a href='http://nsmwiki.org/Sguil_Client'>Sguil client page on NSMwiki</a>.<br>
</li><li>On the server running the Sguil database, set the DAYSTOKEEP variable in /etc/nsm/securityonion.conf to however many days you want to keep in your archive. The default is 365, but you may need to adjust it based on your organization’s detection/response policy and your available disk space.<br>
</li><li>You should also tune <a href='http://code.google.com/p/security-onion/wiki/http_agent'>http_agent</a>.  If you're running ELSA, you already have all the Bro HTTP logs available there, so you might want to disable http_agent to avoid duplicating those logs in the Sguil database:<br>
<pre><code># Terminate the running http_agent<br>
sudo nsm_sensor_ps-stop --only-http-agent<br>
# Disable http_agent<br>
sudo sed -i 's|HTTP_AGENT_ENABLED="yes"|HTTP_AGENT_ENABLED="no"|g' /etc/nsm/*/sensor.conf<br>
</code></pre>
</li><li><a href='DisablingProcesses.md'>Disable any unneeded sensor processes</a>.<br>
</li><li>Tune the number of PF_RING instances for Snort/Suricata and Bro: <a href='PF_RING.md'>PF_RING</a>
</li><li>Optional: exclude unnecessary traffic from your monitoring using <a href='http://code.google.com/p/security-onion/wiki/BPF'>BPF</a>.<br>
</li><li>Optional: add new Sguil user accounts with the following:<br>
<pre><code>sudo nsm_server_user-add<br>
</code></pre>
</li><li>Optional, but highly recommended: configure <a href='Email.md'>email</a> for alerting and reporting.<br>
</li><li>Optional, but highly recommended: place /etc under version control.  If your organization doesn't already have a standard version control tool, you can use <a href='https://help.ubuntu.com/12.04/serverguide/etckeeper.html'>etckeeper</a>:<br>
<pre><code>sudo apt-get install etckeeper bzr<br>
</code></pre>
</li><li>Optional: need “remote desktop” access to your Security Onion sensor or server?  We recommend SSH X-Forwarding as shown above, but if you want something more rdp-like, you can install <a href='http://www.xrdp.org/'>xrdp</a> (sudo apt-get install xrdp) or <a href='http://code.google.com/p/security-onion/wiki/FreeNX'>FreeNX</a>.  Please note that we do not support xrdp or FreeNX.<br>
</li><li>Read more about the tools contained in Security Onion: <a href='http://code.google.com/p/security-onion/wiki/Tools'>Tools</a>