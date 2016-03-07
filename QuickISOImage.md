#### If you just want to quickly evaluate Security Onion using our ISO image (based on Xubuntu 14.04 64-bit): ####
  1. First, review the [Hardware Requirements](Hardware) page.
  1. Review the [Release Notes](Security-Onion-14.04-Release-Notes) page.
  1. [Download and verify our Security Onion ISO image](https://github.com/Security-Onion-Solutions/security-onion/blob/master/Verify_ISO.md).
  1. Boot the ISO image and select the Install option.
  1. Follow the prompts in the Xubuntu installer.  If prompted with an `encrypt home folder` or `encrypt partition` option, **DO NOT** enable this feature.  If asked about automatic updates, **DO NOT** enable automatic updates.  Reboot into your new installation.  Login using the username/password you specified during installation.
  1. Verify that you have Internet connectivity.  If necessary, configure your [proxy settings](Proxy).
  1. [Install updates and reboot.](Upgrade)
  1. Double-click the Setup icon.  The Setup wizard will walk you through configuring `/etc/network/interfaces` and will then reboot.
  1. After rebooting, log back in and start the Setup wizard again.  It will detect that you have already configured `/etc/network/interfaces` and will walk you through the rest of the configuration.  When prompted for Evaluation Mode or Production Mode, choose Evaluation Mode.
  1. Once you've completed the Setup wizard, use the Desktop icons to login to `Sguil`, `Squert`, or `ELSA`.
  1. Finally, review the [Post Installation](PostInstallation) page.