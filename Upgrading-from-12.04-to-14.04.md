#### DISCLAIMERS

* Security Onion 14.04 has not reached *stable* status yet, it's still considered **BETA** software!

* All testing should be done in sacrificial VMs.

* Don't even think of getting this anywhere near your production sensors yet.

* If you test on any kind of production system and it breaks, you get to keep both pieces!

#### PRE-UPGRADE NOTES

* The upgrade process will take at **least** 1-2 hours (per server/sensor), depending on the speed of your server hardware and Internet connection.  Please plan accordingly.

* If you’re upgrading a distributed deployment, you’ll need to perform the steps below on the master server and all sensors, but make sure you start with the master server first!

#### PREPARATION
* Start with a fully configured Security Onion 12.04 installation.
* If running in a VM, create a snapshot so that you can revert if necessary.
* If you're upgrading over ssh and not already running byobu/screen/tmux, start byobu:  
`byobu-enable`

* Ensure all 12.04 updates are installed:  
`sudo soup`

* If soup prompted to reboot, go ahead and do that.  If it didn’t, go
ahead and reboot anyway:  
`sudo reboot`

* Review sostat output to make sure system is healthy before continuing:  
`sudo sostat`

* IMPORTANT! Backup Bro config since it will be removed when Ubuntu removes the package:  
```
sudo sed -i 's|PREV="2.3.2"|PREV="pre-2.4"|g' /var/lib/dpkg/info/securityonion-bro.preinst
sudo /var/lib/dpkg/info/securityonion-bro.preinst install
```

* Verify that Bro config was backed up to /opt/bro/etc_pre-2.4/ (you should have files in this directory):  
`ls -alh /opt/bro/etc_pre-2.4/`

#### UPGRADE FROM UBUNTU 12.04 TO UBUNTU 14.04

* Configure Ubuntu to look for the 14.04 upgrade:  
`sudo sed -i 's|Prompt=never|Prompt=lts|g' /etc/update-manager/release-upgrades`

* Kill xscreensaver (otherwise, do-release-upgrade in the next step will prompt you to do so):  
`sudo pkill xscreensaver`

* Initiate upgrade to Ubuntu 14.04:  
`sudo do-release-upgrade`

* Follow the prompts. If you receive a prompt regarding xscreensaver, select OK. You may receive prompts regarding files that have changed like the following:  
/etc/sudoers  
/etc/apache2/mods-available/ssl.conf  
/etc/apache2/apache2.conf  
/etc/apache2/ports.conf  
/etc/php5/apache2/php.ini  
/etc/xdg/xdg-xubuntu/menus/xfce-applications.menu  
These are files that Security Onion modifies and you may receive prompts for additional files that you have modified. The safest option for each of these is to choose to install the package maintainer’s version. This will back up the existing file in case you need to review it later for any custom modifications you had made.  
* When prompted to restart, press Y to continue.
* If running in a VM, perform a snapshot.

#### ADD BACK SECURITY ONION PACKAGES

* After rebooting, log back in, open a terminal, and add our TEST repo:  
`sudo add-apt-repository ppa:securityonion/test`

* Update all packages that are currently installed:  
`sudo soup`

* Add back any missing Security Onion packages by installing the securityonion-iso metapackage.  If you didn't install from our ISO and instead installed from your preferred flavor of Ubuntu and added our PPA and packages, then you may not necessarily need to install the securityonion-iso metapackage. In the command below, you can replace securityonion-iso with the same Security Onion metapackage(s) you originally installed (securityonion-server, securityonion-sensor, securityonion-elsa, securityonion-all, etc).:  
`sudo apt-get install securityonion-iso syslog-ng-core`  
**IMPORTANT!** If you receive a prompt regarding syslog-ng.conf, press N to keep your currently-installed version.  

#### CLEAN UP

* Remove any unnecessary packages:  
`sudo apt-get autoremove`

* Reboot:  
`sudo reboot`

#### VERIFY

* Log back in and verify all services are working properly.

* If you had created your own ELSA query menu at /var/www/elsa/local.php and it wasn't automatically migrated to /var/www/so/elsa/local.php, then you can copy it:
`sudo cp /var/www/elsa/local.php /var/www/so/elsa/local.php`
You may also need to adjust any links to match the new URL structure.  Replace `<a href="https://<?php echo $_SERVER['HTTP_HOST']; ?>:3154/?` with this `<a href="/elsa-query/?`
* Run sostat and look for anything out of the ordinary:  
`sudo sostat`

* Check log files for anything out of the ordinary.