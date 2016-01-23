#### Release Notes

- As always, make sure you verify the checksum of the downloaded ISO image:  
https://github.com/Security-Onion-Solutions/security-onion/blob/master/checksums.txt

- The ISO boot menu no longer has the Live Desktop option.  Instead, choose the Install option to go directly to the installer (or simply wait 10 seconds for it to automatically boot into the installer).

- On the "Installation type" screen, please select the "Use LVM" option, as this will automatically create a /boot partition at the beginning of the drive and will give you more flexibility later.

- The Keyboard Layout screen may be larger than your screen resolution and so the Continue button may be off the screen to the right like this:  
https://launchpadlibrarian.net/207213663/Screenshot_wilyi386deskmanual_2015-05-22_13%3A05%3A41.png  
You can simply slide the window over until you see the Continue button.  For more information, please see:  
https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1458039

- Once the installer completes, it should prompt to remove installation media and press ENTER.  If instead it appears to hang, simply press the ENTER key to reboot.  If that doesn't work, you may forcibly restart the machine.

- Once you've logged into your newly installed Security Onion, you'll notice that there is only a Setup icon on the desktop.  Icons for Sguil/Squert/ELSA will be created when you run Setup.

- When you run Setup, the Quick Setup and Advanced Setup options have been renamed.  Quick Setup is now called Evaluation Mode.  Advanced Setup is now called Production Mode.  

- When choosing Evaluation Mode, ELSA is now enabled by default.

- When choosing Production Mode, you then have the option of Best Practices or Custom.  Best Practices asks a smaller number of questions and chooses the services that most folks want.  Custom asks all questions just as Advanced Setup used to.

- Setup now defaults to [Best Practices](Best-Practices) so it automatically disables prads, pads_agent, sancp_agent, argus, and http_agent since most users don't need these services.  If you need these services, you can choose Production Mode, then choose Custom, and it will ask if you want to enable them.  Alternatively, you can enable them after Setup has completed in /etc/nsm/HOSTNAME-SENSOR/sensor.conf.

- Once you've completed both phases of Setup, you should see the new icons on your Desktop for Sguil, Squert, and ELSA.  As a reminder, Snorby has been removed from this release.

- ELSA charts now work out of the box with the standard Chromium browser (no more Flash requirement).

- ELSA dashboards now work with no Internet access (no more Google Visualization requirement).

- For more information, please refer to the full [Installation](Installation) guide and other documentation on the Wiki.