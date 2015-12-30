#### PRE-UPGRADE NOTES

If you’re upgrading a distributed deployment, you’ll need to perform the steps below on the master server and all sensors, but make sure you start with the master server first!

If upgrading over ssh, please consider running byobu/screen/tmux to ensure that if your ssh connection drops your system will continue the upgrade process.

#### PREPARATION
* start with a fully configured Security Onion 12.04 installation
* if possible, create a VM snapshot so that you can revert if necessary
* backup Bro config since it will be removed when Ubuntu removes the package
```
sudo sed -i ’s|PREV=“2.3.2”|PREV=“pre-2.4”|g’ /var/lib/dpkg/info/securityonion-bro.preinst
sudo /var/lib/dpkg/info/securityonion-bro.preinst install
```
* ensure all 12.04 updates are installed:
```
sudo soup
```

* if soup prompted to reboot, go ahead and do that.  If it didn’t, go
ahead and reboot anyway:
```
sudo reboot
```

* make sure system is healthy before continuing


#### UPGRADE FROM UBUNTU 12.04 TO UBUNTU 14.04

* configure Ubuntu to look for the 14.04 upgrade:
```
sudo sed -i ‘s|Prompt=never|Prompt=lts|g’ /etc/update-manager/release-upgrades
```

* kill xscreensaver (otherwise, do-release-upgrade will prompt you to do so)
```
sudo pkill xscreensaver
```

* initiate upgrade to 14.04:
```
sudo do-release-upgrade
```

* follow the prompts
* if you receive a prompt regarding xscreensaver, select OK
* you may receive prompts regarding files that have changed like the following:
/etc/sudoers
Apache’s ssl.conf
Apache’s apache2.conf
Apache’s ports.conf
php.ini
xfce-applications.menu
These are files that Security Onion modifies and you may receive prompts for additional files that you have modified.
The safest option for each of these is to press Y to install the package maintainer’s version.
This will back up the existing file in case you need to review it later for any custom modifications you had made.
* When prompted to restart, press Y to continue


#### SNAPSHOT IF RUNNING IN A VM

#### ADD BACK SECURITY ONION PACKAGES

* after reboot, log back in, open a terminal, and add my DEVELOPMENT repo:
```
sudo add-apt-repository ppa:doug-burks/trusty
```

* update all packages that are currently installed:
```
sudo soup
```

* add back any missing security onion packages:
```
sudo apt-get install securityonion-iso syslog-ng-core
```

* IMPORTANT! If you receive a prompt regarding syslog-ng.conf, press N to keep your current copy

* remove any unnecessary packages:
```
sudo apt-get autoremove
```

* reboot:
```
sudo reboot
```

* log back in and verify all services are working properly

* check sostat and log files for anything out of the ordinary