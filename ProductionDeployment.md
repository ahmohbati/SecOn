#### If you're going to be deploying Security Onion in production, follow these steps: ####
  1. First, check the [Hardware Requirements](Hardware) page.
  1. [Download and verify the Security Onion ISO image](https://github.com/Security-Onion-Solutions/security-onion/blob/master/Verify_ISO.md) OR download and verify the ISO image for your preferred flavor of Ubuntu 14.04 32-bit/64-bit.  
  1. If deploying a distributed environment (a master server and one or more slave sensors), you’ll need to perform the remaining steps on the server and all sensors, but make sure you install/configure the master server first.  For best performance, the master server should be dedicated to just being a server for the other sensor boxes (the master server should have no sniffing interfaces of its own).  Please note that sensors need to connect to the master server on ports 22 and 7736.  If you choose to enable salt for sensor management, they will also need to be able to connect to the master server on ports 4505 and 4506.<br>
  1. Using the downloaded ISO, install the operating system. If prompted with an "encrypt home folder" option, DO NOT enable this feature.  If asked about automatic updates, DO NOT enable automatic updates.  If prompted to install any additional packages, the only option you should choose is OpenSSH Server (openssh-server). Specifically, do NOT choose MySQL. All other required dependencies will be installed automatically.<br>
  1. When asked about partitioning, there are a few things to keep in mind:  
      * If you have more than 2TB of disk space, you will probably want to create a dedicated `/boot` partition at the beginning of the disk to ensure that you don’t have any Grub booting issues.  Choosing the LVM option should do this automatically.  
      * Check to see if the installer allocates a large amount of space to /home. If this is the case, you may want to shrink /home to give more space to /.<br>
      * The Sguil database on the server (doesn’t exist on sensor-only installations) can grow fairly large (100GB or more for decent-size networks). It’s stored at `/var/lib/mysql/`, so you may want to put /var on a dedicated partition/disk and assign a good amount of disk space to it. Also see the `DAYSTOKEEP` instructions on the [Post-Installation page](https://github.com/Security-Onion-Solutions/security-onion/wiki/PostInstallation).<br>
      * Sensors store full packet captures at `/nsm/sensor_data/`, so you may want to put `/nsm` on a dedicated partition/disk and assign as much disk space as possible (1TB or more). For larger volumes you might also consider using XFS for the `/nsm` partition.<br>
  1. When installation completes, reboot into your new installation and login with the credentials you specified during installation.<br>
  1. If you’re running a VM, now would be a good time to snapshot it so you can revert later if you need to.<br>
  1. Verify that you have Internet connectivity. If necessary, configure your [proxy](Proxy) settings</a>.<br>
  1. If you installed from the Security Onion 14.04 ISO image, run `sudo soup`, reboot if prompted, and then skip to the "Setup wizard" step below.<br>
  1. If your machine is running a 32 bit version of Ubuntu and you have more than 4GB of RAM, <a href='https://help.ubuntu.com/community/EnablingPAE'>install the PAE kernel</a>.<br>
  1. Install all Ubuntu updates and reboot:  
```sudo apt-get update && sudo apt-get dist-upgrade && sudo reboot```
  1. Log back in and configure MySQL not to prompt for root password:<br>
`echo "debconf debconf/frontend select noninteractive" | sudo debconf-set-selections`
  1. Install software-properties-common if it's not already installed:<br>
`sudo apt-get -y install software-properties-common`
  1. Add the Security Onion stable repository:<br>
`sudo add-apt-repository -y ppa:securityonion/stable`
  1. Update:<br>
`sudo apt-get update`
  1. Install the securityonion-all metapackage (or one of the more focused [metapackages](MetaPackages)). This could take 15 minutes or more depending on the speed of your CPU and Internet connection.<br>
`sudo apt-get -y install securityonion-all syslog-ng-core`
  1. OPTIONAL: If you want to use [Salt](Salt) to manage your deployment, also install securityonion-onionsalt.  You can do this before or after Setup, but it's much easier if you do it before Setup.<br>
`sudo apt-get -y install securityonion-onionsalt`
  1. Run the Setup wizard.  If you are locally on the box, you can run the GUI:  
`sudo sosetup`  
Otherwise, if you are remote and logged in over ssh, you can run CLI-only Setup using sosetup.conf.  For more information, please see /usr/share/securityonion/sosetup.conf.
  1. The Setup wizard will walk you through configuring `/etc/network/interfaces` and will then reboot.<br>
  1. When prompted whether you would like to configure `/etc/network/interfaces` now, choose “Yes, configure /etc/network/interfaces!.”<br>
  1. If you have more than one network interface, you’ll be asked which to specify which one should be the management interface.<br>
  1. You’ll then be asked to choose DHCP or static addressing for the management interface. It is highly recommended you choose static.<br>
  1. Choosing static, you’ll be prompted to enter a static IP address for your management interface, the network’s subnet mask, gateway IP address, DNS server IP addresses (separated by spaces), and your local domain.<br>
  1. You’ll then be prompted to select any additional interfaces that will be used for sniffing/monitoring network traffic.<br>
  1. When prompted, choose “Yes, make changes!"<br>
  1. If you need to adjust any network settings manually (e.g. `MTU`), you may edit `/etc/network/interfaces` before rebooting.<br>
  1. When ready to reboot, click "Yes, reboot!”<br>
  1. After rebooting, log back in and start the Setup wizard again (GUI if local, sosetup.conf CLI if remote). It will detect that you have already configured /etc/network/interfaces and will walk you through the rest of the configuration.<br>
  1. Select Production Mode.<br>
  1. Choose whether the host being configured will be Standalone, Server, or Sensor.  If deploying a distributed environment (a master server and one or more slave sensors), the master server should be dedicated to just being a server for the other sensor boxes (the master server should have no sniffing interfaces of its own).  So the first box should be configured using "Server" and the remaining boxes should be configured using "Sensor".<br>
      * Standalone<br>
        * You will be prompted to specify which IDS Engine (Snort or Suricata) you would like to use.<br>
        * If you have multiple CPU cores available, the Best Practices option should automatically assign an equal number of IDS and Bro processes based on your number of CPU cores.  If instead of Best Practices you choose Custom, then you'll be prompted to designate how many IDS and Bro processes you would like to run. (These settings can be modified later by changing the `IDS_LB_PROCS` variable in `/etc/nsm/$HOSTNAME-$INTERFACE/sensor.conf` and the `lb_procs` variable in `/opt/bro/etc/node.cfg`, respectively).<br>
        * You’ll be asked which IDS ruleset you would like to use.<br>
        * You will then be prompted for user account information for Sguil, Squert, and ELSA.<br>
        * You’ll be prompted to proceed with making the changes to setup Security Onion.<br>
      * Server<br>
        * You will be prompted to specify which IDS Engine (Snort or Suricata) you would like to use.<br>
        * You’ll be asked which IDS ruleset you would like to use.<br>
        * You will then be prompted for user account information for Sguil, Squert, and ELSA.<br>
        * You’ll be prompted to proceed with making the changes to setup Security Onion.<br>
      * Sensor<br>
        * You will be prompted for an SSH account on the master server that has sudo privileges. (Note: the management interface on the sensor must be able to SSH to the management interface on the server, so please make sure that your server has been set up and you have network connectivity and no firewall rules that would block this traffic.) Consider creating a separate SSH account on the master server for each sensor so that if a sensor is ever compromised, its individual account can be disabled without affecting the other sensors. To do this, create a new user using the `sudo adduser $user` command (replacing $user with the actual username).  (The new account must have a full home directory. If you do not create it when you create the account, copy `/etc/skel` to `/home/$user` and do `chown -R $user:$user /home/$user`. This is needed so the .ssh directory may be created to manage the connection.)  Then add the new user to the sudo group with the `sudo adduser $user sudo` command. Once Setup is complete, the user can be removed from the sudo group with the `sudo deluser $user sudo` command.<br><br>For example, suppose you’re setting up a server and two separate sensors and you want to use sensor1 as the SSH username for the first sensor and sensor2 as the SSH username for the second sensor (these are just examples, you should replace sensor1 and sensor2 with your own usernames):<br>
          * SERVER<br>
            * run through sosetup, choosing Production Mode and choosing Server only (no sniffing)<br>
          * FIRST SENSOR - username sensor1<br>
            * create an account on the SERVER called sensor1:<br>
`sudo adduser sensor1`
            * add the new account to the sudo group:<br>
`sudo adduser sensor1 sudo`
            * run through sosetup on the SENSOR<br>
            * on the SERVER, remove the account from the sudo group (but leave the account active):<br>
`sudo deluser sensor1 sudo`
          * SECOND SENSOR - username sensor2<br>
            * create a second account on the SERVER and add it to the sudo group:<br>
`sudo adduser sensor2`
            * add the new account to the sudo group:<br>
`sudo adduser sensor2 sudo`
            * run through SETUP on the second SENSOR<br>
            * on the SERVER, remove the account from the sudo group (but leave the account active):<br>
`sudo deluser sensor2 sudo`
        * You’ll be asked which network interface should be monitored.<br>
        * If you have multiple CPU cores available, the Best Practices option should automatically assign an equal number of IDS and Bro processes based on your number of CPU cores.  If instead of Best Practices you choose Custom, then you'll be prompted to designate how many IDS and Bro processes you would like to run. (These settings can be modified later by changing the `IDS_LB_PROCS` variable in `/etc/nsm/$HOSTNAME-$INTERFACE/sensor.conf` and the `lb_procs` variable in `/opt/bro/etc/node.cfg`, respectively).


Proceed to [PostInstallation](PostInstallation).