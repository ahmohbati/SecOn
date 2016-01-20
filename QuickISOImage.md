#### If you just want to quickly evaluate Security Onion using our ISO image (based on Xubuntu 14.04 64-bit): ####
  1. First, review the [Hardware Requirements](Hardware) page.
  1. Review the [Release Notes](Security-Onion-14.04-Release-Notes) page.
  1. Download the ISO image from our [Releases](https://github.com/Security-Onion-Solutions/security-onion/releases) page.
  1. Once the ISO image download has completed, verify the checksums as shown here: https://github.com/Security-Onion-Solutions/security-onion/blob/master/checksums.txt
  1. At the boot menu, select the Install option.
  1. Follow the prompts in the Xubuntu installer.  If prompted with an `encrypt home folder` option, **DO NOT** enable this feature.  If asked about automatic updates, **DO NOT** enable automatic updates.  Reboot into your new installation.  Login using the username/password you specified during installation.
  1. Verify that you have Internet connectivity.  If necessary, configure your [proxy settings](Proxy).
  1. [Install updates and reboot.](Upgrade)
  1. Double-click the Setup icon.  The Setup wizard will walk you through configuring `/etc/network/interfaces` and will then reboot.
  1. After rebooting, log back in and start the Setup wizard again.  It will detect that you have already configured `/etc/network/interfaces` and will walk you through the rest of the configuration.
  1. Once you've completed the Setup wizard, use the Desktop icons to login to `Sguil`, `Squert`, or `ELSA`.
  1. Finally, review the [Post Installation](PostInstallation) page.