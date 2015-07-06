#### If you just want to quickly evaluate Security Onion using our ISO image (based on Xubuntu 12.04 64-bit): ####
  1. First, review the [Hardware Requirements](Hardware) page.
  1. Download the ISO image from <a href="https://sourceforge.net/projects/security-onion/files/12.04.5.2/">Sourceforge</a> or via <a href='http://port111.com/securityonion-12.04.5.2-20150617.iso.torrent'>Torrent</a>.
  1. Once the ISO image download has completed, verify the checksums as shown here: http://blog.securityonion.net/2015/07/security-onion-120452-iso-image-now.html
  1. Boot the ISO image into the Live Desktop environment and then double-click the Install icon on the desktop.
  1. Follow the prompts in the Xubuntu installer.  If prompted with an `encrypt home folder` option, **DO NOT** enable this feature.  If asked about automatic updates, **DO NOT** enable automatic updates.  Reboot into your new installation.  Login using the username/password you specified during installation.
  1. Verify that you have Internet connectivity.  If necessary, configure your [proxy settings](Proxy).
  1. [Install updates and reboot.](Upgrade)
  1. Double-click the Setup icon.  The Setup wizard will walk you through configuring `/etc/network/interfaces` and will then reboot.
  1. After rebooting, log back in and start the Setup wizard again.  It will detect that you have already configured `/etc/network/interfaces` and will walk you through the rest of the configuration.
  1. Once you've completed the Setup wizard, use the Desktop icons to login to `Sguil`, `Squert`, `Snorby` or `ELSA`.

Please review the [Post Installation](PostInstallation) page.