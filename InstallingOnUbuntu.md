#### If you want to quickly evaluate Security Onion on your preferred flavor of Ubuntu 14.04 32-bit/64-bit (not using our ISO image), follow these steps: ####
  1. First, check the [Hardware Requirements](Hardware) page.
  1. Download the ISO image for your preferred flavor of Ubuntu 14.04.5, verify its checksum,  and boot from it.<br>
  1. Follow the prompts in the installer, but see the two notes below first.<br>
  1. When prompted to `encrypt home folder` option, **DO NOT** enable this feature.<br>
  1. When asked about automatic updates, **DO NOT** enable automatic updates.<br>
  1. Reboot into your new installation.<br>
  1. Login using the username/password you specified during installation.<br>
  1. Verify that you have Internet connectivity.  If necessary, configure your [proxy](Proxy) settings</a>.<br>
  1. Log back in (using `ssh -X` if you’re installing on Ubuntu Server or a headless distro).<br>
  1. Configure `MySQL` not to prompt for root password:<br>

    ````
echo "debconf debconf/frontend select noninteractive" | sudo debconf-set-selections
    ````
  1. Clean apt list repository:

    ````
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
    ````
  1. Add the Security Onion stable repository:<br>

    ````
sudo apt-get -y install python-software-properties
sudo add-apt-repository -y ppa:securityonion/stable
sudo apt-get update
    ````
  1. Install the securityonion-all metapackage:<br>

    ````
sudo apt-get -y install securityonion-all syslog-ng-core
    ````
  1. If you installed a fresh copy of Ubuntu, you can most likely skip this step.  Otherwise, you may need to add your IP address to the /etc/hosts.allow file and flush iptables (if you don't do this, you may not be able to SSH in):<br>

    ````
sudo gedit /etc/hosts.allow 
    ````
add line:
    ````
sshd: xxx.xxx.xxx.xxx/255.255.255.255
    ````
Flush IPTables (sosetup will configure properly)
    ````
iptables -F
    ````

  1. Run the Setup wizard:<br>

    ````
sudo sosetup
    ````
  1. Follow the prompts.<br>
  1. Analyze alerts using the Sguil client, or open a browser to <a href='https://localhost'>https://localhost</a> where you can access `Squert` and `ELSA`.<br>
  1. Follow the [upgrade](Upgrade) process.

Please review the [PostInstallation](PostInstallation) page.
