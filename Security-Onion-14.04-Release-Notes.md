#### Release Notes

- The ISO boot menu no longer has the Live Desktop option.  Instead,
choose the Install option to go directly to the installer.

- The installer now supports LVM, which automatically creates a /boot
partition and will likely be our recommended option.

- The Keyboard Layout page may be larger than your screen resolution and so the Next button may be hidden.  You can simply slide the window over until you see the Next button.

- Once the installer completes, it should prompt to eject the media.
If you don't see any text but it appears to hang, simply press Enter
to eject the media and reboot.

- Once you've logged into your newly installed Security Onion, you'll
notice that there is only a Setup icon on the desktop.  Icons for
Sguil/Squert/ELSA will be created when you run Setup.

- Quick Setup is now called Evaluation Mode.  When choosing Quick
Setup, ELSA is now enabled by default.

- Advanced Setup is now called Production Mode.  When choosing
Production Mode, you then have the option of Best Practices or Custom.
Best Practices asks a smaller number of questions and chooses the
services that most folks want.  Custom asks all questions just as
Advanced Setup used to.

- Once you've completed both phases of Setup, you should see the new
icons on your Desktop for Sguil, Squert, and ELSA.  As a reminder,
Snorby has been removed from this release.

- ELSA charts now work out of the box with the standard Chromium
browser (no more Flash requirement).

- ELSA dashboards now work with no Internet access (no more Google
Visualization requirement).