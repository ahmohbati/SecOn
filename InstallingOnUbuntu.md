#### If you want to quickly evaluate Security Onion on your preferred flavor of Ubuntu 14.04 32-bit/64-bit (not using our ISO image), follow these steps: ####
  1. First, check the [Hardware Requirements](Hardware) page.
  1. Download the ISO image for your preferred flavor of Ubuntu 14.04, verify the ISO image,  and boot from it.
  1. Follow the prompts in the installer.  When prompted to `encrypt home folder` or `encrypt partition` option, **DO NOT** enable this feature.  When asked about automatic updates, **DO NOT** enable automatic updates.
  1. Reboot into your new installation.
  1. Login using the username/password you specified during installation.
  1. Verify that you have Internet connectivity.  If necessary, configure your [proxy](Proxy) settings</a>.
  1. Log back in (using `ssh -X` if you’re installing on Ubuntu Server or a headless distro).
  1. Configure `MySQL` not to prompt for root password:<br>
```echo "debconf debconf/frontend select noninteractive" | sudo debconf-set-selections```
  1. Clean apt list repository:<br>
`sudo rm -rf /var/lib/apt/lists/*`<br>
`sudo apt-get update`
  1. Add the Security Onion stable repository:<br>
`sudo apt-get -y install software-properties-common`<br>
`sudo add-apt-repository -y ppa:securityonion/stable`<br>
`sudo apt-get update`
  1. Install the securityonion-all metapackage:<br>
`sudo apt-get -y install securityonion-all syslog-ng-core`
  1. Run the Setup wizard:<br>
`sudo sosetup`
  1. Follow the prompts.<br>
  1. Analyze alerts using the Sguil client, or open a browser to <a href='https://localhost'>https://localhost</a> where you can access `Squert` and `ELSA`.<br>
  1. Follow the [upgrade](Upgrade) process.

Please review the [PostInstallation](PostInstallation) page.
