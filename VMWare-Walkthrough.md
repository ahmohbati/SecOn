####This tutorial was written to address setting up Security Onion 14.04 in VMWare Workstation Pro 12 (although this should be similar for most VMWare installations).###

If you don't have VMWare Workstation, you could also use VMWare Player, found here:

http://www.vmware.com/products/player/playerpro-evaluation.html  


####Follow the steps below to setup a standalone machine in Evaluation Mode:#####
  1. Obtain and verify the latest Security Onion ISO, found here:  
https://github.com/Security-Onion-Solutions/security-onion/blob/master/Verify_ISO.md
  1. From VMWare, select File >> New Virtual Machine.
  1. Select Typical installation >> "Click Next".
  1. Installer disc image file  >> SO ISO file path >> Click "Next".
  1. Choose Linux, Ubuntu 64-Bit and click "Next".
  1. Specify virtual machine name and click "Next".
  1. Specify maximum disk size (min 20GB), store as single file, click Next.
  1. Customize hardware:
   1. Memory – 3GB
   1. Processors – 2/1 core each
   1. Network Adapter (NAT or Bridged -- if you want to be able to access your Security Onion machine from other devices in the network, then choose Bridged, otherwise choose NAT to leave it behind the host) -- in this tutorial, this will be the management interface.
   1. Add >> Network Adapter (Bridged) - in this tutorial, this will be the sniffing (monitor) interface.
  1. Click "Close".
  1. Click "Finish".
  1. Power on the virtual machine.
  1. Wait for boot or press enter while selecting “Install”.
  1. From the Welcome Screen, select language and click "Continue".
  1. Click “Continue”.
  1. Select "Use LVM with the new SecurityOnion installation" (or "Erase existing disk…").
  1. Click "Install Now".
  1. Confirm changes and click "Install Now".
  1. From the "Where are you?" prompt, select your time zone and click "Continue".
  1. Drag the window to the left (Ubuntu 14.04 bug), and click "Continue".
  1. Enter your name.
  1. Enter your computer’s name.
  1. Select a username and enter a password.
  1. Click "Continue".
  1. Click "Restart Now".
  1. (Optional) Adjust display settings >> Terminal Icons, Settings >> Display > Choose and confirm resolution.   


#### Soup

  1. Before running Setup, ensure you run "soup" to ensure you have the latest updates:
   1. Enter terminal and type the following: `sudo soup -y`.
   1. You may be prompted to reboot.  If so, reboot, and continue to the next step.

#### Setup: Phase 1

  1. Click the Security Onion "Setup" icon on the desktop.
  1. You will be prompted to enter an administrative password (same one you defined during the install).  Enter it here and click "OK".
  1. Setup will ask if you would like to continue.  Click "Yes, Continue!".
  1. Setup will ask if you would like to configure /etc/network/interfaces. Click "Yes, configure /etc/network/interfaces!".
  1. Setup will ask which network interface should be the management interface.  Select the desired interface and click "OK". 
  1. Setup will ask if you would like to use static or DHCP addressing.  The quickest and easiest option would be to use DHCP (if it is available, however, for production installs, you may want to use static).  Choose your desired addressing type and click "OK".
  1. Setup will ask if you would like to configure sniffing (monitor) interfaces.  Click "Yes, Configure sniffing interfaces."
  1. Setup will ask which interfaces should be used for sniffing.  Select the desired interface(s) and click "OK".
  1. Setup will present a summary of the changes to be made to the interface configuration.  If correct, click "Yes, make changes!".
  1. Set up will ask to reboot so that changes to the configuration can be completed.  Click "Yes, reboot!".  

#### Setup: Phase 2

   1. After the machine reboots, click the Security Onion 'Setup" icon.
   1. You will be prompted to enter an administrative password (same one you defined during the install).  Enter it here and click "OK".
   1. Setup will ask if you would like to continue.  Click "Yes, Continue!".
   1. Setup will ask if you would like to skip network configuration.  If you are satisfied with the configuration you specified earlier, click "Yes, skip network configuration."
   1. Setup will ask if you would like to configure "Evaluation Mode" or "Production Mode".  For testing, you can simply configure "Evaluation Mode", otherwise, choose "Production Mode" to configure a number of options.  In this tutorial, we will choose "Evaluation Mode" for simplicity.  This will configure a single instance of Snort and Bro.  Select "Evaluation Mode" and click "OK".
   1. Setup will ask which interface(s) should be monitored.  Select the desired interfaces(s) and click "OK".
   1. Setup will ask what username and password you would like to configure to access Sguil, Squert, and ELSA.  Enter the username and password, and verify the password, clicking "OK" at each prompt.
   1. Setup will present you with a summary of changes to be made upon confirmation.  If you are satisfied with the presented changes, click "Yes, proceed with the changes!".  

####Relax!

It's all over -- now that wasn't so bad, was it?  After setup is complete, you should be presented with several dialogs, offering suggestions and useful information, such as:

* Setup log - can be found in /var/log/nsm/sosetup.log.
* IDS Alerts can be found in Sguil, Squert, and ELSA.  
https://github.com/Security-Onion-Solutions/security-onion/wiki/Sguil  
https://github.com/Security-Onion-Solutions/security-onion/wiki/Squert  
https://github.com/Security-Onion-Solutions/security-onion/wiki/ELSA  

* Bro logs can be found in /nsm/bro.  
https://github.com/Security-Onion-Solutions/security-onion/wiki/Bro

* Security Onion Install information can be found via sostat:
 * "sudo sostat" - will give you detailed information about your service status.
 * "sudo sostat-quick"  - will give you a guided tour of the sostat output.
 * "sudo sostat-redacted" - will give your redacted information of your sostat output, suitable for sharing on the mailing list, should you have issues.  

* Rules downloaded by PulledPork will be stored in /etc/nsm/rules/downloaded.rules.
* Local rules can be added to /etc/nsm/rules/local.rules.
* Rules can be modified by Pulledpork through the use of the files in /etc/nsm/pulledpork/.
* Rules are updated every morning, however, you can manually update them by running "sudo rule-update".
* More information about managing alerts/rules can be found here:  
https://github.com/Security-Onion-Solutions/security-onion/wiki/ManagingAlerts
https://github.com/Security-Onion-Solutions/security-onion/wiki/AddingLocalRules

* Sensors can be tuned by modifying the files in /etc/nsm/[hostname-interface].

* NOTE: The local firewall (ufw) is locked down by default to only allow connections to port 22.  You can run "sudo so-allow" to add exceptions for analysts, ossec agents, etc.  
See the following for more information:
https://github.com/Security-Onion-Solutions/security-onion/wiki/Firewall

* For more information, consult the FAQ or the wiki:  
https://github.com/Security-Onion-Solutions/security-onion/wiki/FAQ  
https://github.com/Security-Onion-Solutions/security-onion/wiki

* Questions or problems can be submitted to the mailing list:
https://groups.google.com/forum/#!forum/security-onion

####Things to keep in mind

* With the sniffing interface in "bridged" mode, you will be able to see all traffic to/from the host machine's physical NIC.  If you would like to see **ALL** the traffic on your network, you will need a method of forwarding that traffic to the interface to which the virtual adapter is bridged.  This can be achieved by switch port mirroring (SPAN), or through the use of an (inline) tap.