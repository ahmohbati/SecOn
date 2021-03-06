Snorby is no longer included in Security Onion as of Security Onion 14.04.  

#### Introduction ####

This page will walk you through wiping the Snorby database.  This only pertains to the Snorby database and does not affect the Sguil database, the ELSA database, or any other data/config.

As of 2015/01/06, we have a new utility called so-snorby-wipe which should handle this for you:

http://blog.securityonion.net/2015/01/new-nsm-and-setup-packages-resolve.html

So you should be able to simply run the following:
```
sudo so-snorby-wipe
```
and follow the prompts.

If you need to run this process manually, then see the steps below.

#### Details ####

The details below came from Kevin Branch in this mailing list thread:
https://groups.google.com/d/topic/security-onion/m4uu2PSa_eg/discussion

Quoting Kevin Branch:

> I recently had a problem with a broken Snorby database that was jamming barnyard2 and thus breaking pretty much anything Suricata-alert related in my SO system.  My final solution was to completely wipe out the Snorby application along with it's data and start fresh.  I did not want to rebuild SO.  This is the method that worked well for me, and since I seem to remember someone asking a while back about resetting Snorby while leaving SO intact, I offer it here to the wider group.  Refinements are welcome.

> The following procedure will completely wipe out all of your Snorby data and any custom configurations you have made to Snorby,  restoring Snorby to like-new condition while leaving the rest of SO alone.  I have only tested this on a standalone install of SO.

> Get to the CLI of your SO box.

```
# Become root
sudo su -

# shut down NSM services
service nsm stop

# adapt these two lines to reflect your existing local snorby credentials and then run them
SNORBY_EMAIL="***EMAIL ADDR HERE***"
SGUIL_CLIENT_PASSWORD_1="***PASSWORD HERE***"

# these are needed by the script below
LOG=log.txt
ELSA=YES

# run this code section which was lifted directly from sosetup 

# Kill any existing Snorby processes.
pkill delayed_job
# Delete any existing Snorby data.
if [ -d /var/lib/mysql/snorby ]; then
mysql -e "drop database snorby" >> $LOG 2>&1
fi
# Set email and password
cp /opt/snorby/db/seeds.rb.securityonion /opt/snorby/db/seeds.rb
sed -i "s|ReplaceWithDesiredEmail|$SNORBY_EMAIL|g" /opt/snorby/db/seeds.rb
sed -i "s|ReplaceWithDesiredPassword|$SGUIL_CLIENT_PASSWORD_1|g" /opt/snorby/db/seeds.rb
# Set FPC options
IP=`ifconfig |grep "inet addr" | awk '{print $2}' |cut -d\: -f2 |grep -v "127.0.0.1" |head -1`
sed -i "s|packet_capture_url, nil|packet_capture_url, 'https://$IP/capme/'|g" /opt/snorby/db/seeds.rb
sed -i "s|packet_capture, nil|packet_capture, 1|g" /opt/snorby/db/seeds.rb
sed -i "s|packet_capture_auto_auth, 1|packet_capture_auto_auth, nil|g" /opt/snorby/db/seeds.rb
# Initialize Snorby DB
su www-data -c "cd /opt/snorby; bundle exec rake snorby:setup RAILS_ENV=production" >> $LOG 2>&1
# Shred the Snorby password
shred -u /opt/snorby/db/seeds.rb >> $LOG 2>&1
# Pivot from Snorby to ELSA
[ "$ELSA" = "YES" ] && mysql -uroot -Dsnorby -e "INSERT INTO lookups (title,value) VALUES('ELSA Search By IP Address','https://$IP:3154/?query_string=\"\${ip}\"%20groupby:program')"

# review the log if you wish
less log.txt

# update Snorby's reference tables
rule-update

# get a fresh start
reboot
```