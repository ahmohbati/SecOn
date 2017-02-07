#### Setup now includes sosetup-email
As of [securityonion-setup - 20120912-0ubuntu0securityonion222](http://blog.securityonion.net/2016/07/securityonion-setup-20120912.html), the Setup package now includes a script called so-email, which will automatically configure automated server-side email for you as described below.  Simply run the following command then follow the prompts:  
`sudo so-email`

To automate email setup, copy and modify the example file located at `/usr/share/securityonion/so-email.conf`, then run `so-email` with the `-f` flag:<br> 

`sudo so-email -f ~/so-email.conf`

#### Sguil client
Please note that the Sguil client has its own email configuration (separate from the Sguil server) which can be modified in `/etc/sguil/sguil.conf`.

#### Introduction ####

This page describes how to configure email for alerting and reporting.  Applications such as Sguil and OSSEC have their own mail configuration and don't rely on a mail server in the OS itself.  However, you may still want to install a mail server in the OS so that you can get daily emails from the sostat script and from Bro.

####How do I configure the OS itself to send emails?####
Install and configure your favorite mail server.  Depending on your needs, this could be something simple like `nullmailer` (recommended) or something more complex like `exim4`.<br>
<br>
Here are some `nullmailer` instructions provided by Michael Iverson:<br>
<pre><code>sudo apt-get install nullmailer<br>
# edit /etc/mailname to hold your "from" domain name. (If you were google, you'd use "gmail.com".)<br>
# edit /etc/nullmailer/adminaddr to contain the address you want mail to root to be routed to.<br>
# edit /etc/nullmailer/remotes to contain the mail server to forward email to. <br>
</code></pre>
Alternatively, here are some instructions for the more complex `exim4`:<br>
<pre><code>sudo apt-get -y install mailutils<br>
sudo dpkg-reconfigure exim4-config<br>
</code></pre>
Once you've configured your mail server and verified that it can send email properly, you might want to create a daily cronjob to execute `/usr/sbin/sostat` and email you the output:<br>
<pre><code># /etc/cron.d/sostat<br>
#<br>
# crontab entry to run sostat and email its output<br>
<br>
SHELL=/bin/sh<br>
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin<br>
EMAIL=YourUsername@YourDomain.com<br>
<br>
01 12    * * *   root    HOSTNAME=`hostname`; /usr/sbin/sostat 2&gt;&amp;1 | mail -s "$HOSTNAME stats" $EMAIL<br>
<br>
</code></pre>

If you don't already have the `mail` utility, you can try installing:<br>
<pre><code>sudo apt-get install mailutils<br>
</code></pre>

#### How do I configure Sguil to send alerts via email?<br>####
Modify `/etc/nsm/securityonion/sguild.email` (on the master server) as needed and restart sguild:
```
sudo nsm_server_ps-restart
```
You can then verify the email configuration by looking at the top of sguild's log file:
```
head -20 /var/log/nsm/securityonion/sguild.log
```
For more information, please see:<br>
<a href='http://nsmwiki.org/Sguil_FAQ#Can_sguil_page_me_when_it_sees_a_particular_alert.3F'><a href='http://nsmwiki.org/Sguil_FAQ#Can_sguil_page_me_when_it_sees_a_particular_alert.3F'>http://nsmwiki.org/Sguil_FAQ#Can_sguil_page_me_when_it_sees_a_particular_alert.3F</a></a>

You may want to install a local mail relay on your master server, configure it to relay mail to your corporate mail server, and then configure Sguil to send email to the local mail relay.

**Please note**: Sguil will only send email alerts for what is considers *new* events. Ensure you classify events within the Sguil console, or consider [creating an Autocat rule](https://github.com/Security-Onion-Solutions/security-onion/wiki/ManagingAlerts#autocategorize-events) to automatically classify them if you prefer to receive emails for all instances of an alert.  Otherwise, you may not receive alerts as intended.

####How do I configure OSSEC to send emails?####
Modify `/var/ossec/etc/ossec.conf` as follows:<br>
<pre><code>  &lt;global&gt;<br>
    &lt;email_notification&gt;yes&lt;/email_notification&gt;<br>
    &lt;email_to&gt;YourUsername@YourDomain.com&lt;/email_to&gt;<br>
    &lt;smtp_server&gt;YourMailRelay.YourDomain.com&lt;/smtp_server&gt;<br>
    &lt;email_from&gt;ossec@YourDomain.com&lt;/email_from&gt;<br>
    &lt;email_maxperhour&gt;100&lt;/email_maxperhour&gt;<br>
  &lt;/global&gt;<br>
</code></pre>
Then restart OSSEC:<br>
<pre><code>sudo service ossec-hids-server restart<br>
</code></pre>

####How do I configure ELSA to send emails?####
Add your email address to the user_info table of the securityonion_db database (replacing FIRSTLAST@YOURDOMAIN.COM with your actual email address and FIRSTLAST with your Sguil/ELSA username):
```
sudo mysql --defaults-file=/etc/mysql/debian.cnf -Dsecurityonion_db -e "update user_info set email='FIRSTLAST@YOURDOMAIN.COM' where username='FIRSTLAST';"
```
Change the following in the "email" section of /etc/elsa_web.conf (replacing YOUR.SECURITY.ONION.BOX with the actual hostname or IP address of your Security Onion master server and replacing MAIL.EXAMPLE.COM with the actual hostname or IP address of your internal mail relay):
```
"base_url" : "https://YOUR.SECURITY.ONION.BOX/elsa-query",
"smtp_server": "MAIL.EXAMPLE.COM",
```
Restart Apache:
```
sudo service apache2 restart
```
You can then have ELSA send an email alert by doing the following:
* run a query
* click "Result Options"
* click "Alert or Schedule"
* choose your parameters and click the Submit button



####How do I configure Bro to send emails?####
Edit `/opt/bro/etc/broctl.cfg` and set the following:<br>
<pre><code>MailTo = YourUsername@YourDomain.com<br>
sendmail = /usr/sbin/sendmail<br>
</code></pre>
Then update and restart Bro:<br>
<pre><code>sudo nsm_sensor_ps-restart --only-bro<br>
</code></pre>

You should then start receiving hourly connection summary emails.  If you don't want the connection summary emails, you can add the following to `broctl.cfg` and update and restart Bro as shown above:<br>
<pre><code>tracesummary=<br>
</code></pre>

You may want to receive emails for Bro notices.  To do that, add the following to `/opt/bro/share/bro/site/local.bro` and update/restart Bro as shown above:<br>
<pre><code>hook Notice::policy(n: Notice::Info)<br>
            {<br>
            add n$actions[Notice::ACTION_ALARM];<br>
            }<br>
</code></pre>
Also see:<br>
<a href='http://mailman.icsi.berkeley.edu/pipermail/bro/2013-December/006418.html'>http://mailman.icsi.berkeley.edu/pipermail/bro/2013-December/006418.html</a>

####How can I get an email alert when my sensor stops seeing traffic?####
If you configured OSSEC or Bro as shown above, they should automatically do this for you.  Another option can be found on the [SensorStopsSeeingTraffic](SensorStopsSeeingTraffic) page.