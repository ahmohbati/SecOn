### Introduction
HWE stands for Hardware Enablement and is Ubuntu's term for kernel and graphics driver support.

### Status
Check to see if your HWE stack is supported:
```
sudo hwe-support-status
```

If it says `Your Hardware Enablement Stack (HWE) is supported until April 2019.`, then no further action is required and you can ignore the rest of the page.  If you got something other than that, then please continue reading!

### Upgrading HWE
If you're running Security Onion 14.04 and you get a WARNING that security updates have ended, you may need to upgrade your HWE stack using the "Ubuntu 14.04 LTS - Trusty Tahr" instructions here:  
https://wiki.ubuntu.com/Kernel/LTSEnablementStack

Before you do that, however, you'll want to run `sudo soup` to ensure that you have all the latest packages installed, including PF_RING to support the latest kernels.

### Example
For example, if you installed your system using our original Security Onion 14.04 ISO images (14.04.3.1, 14.04.4.4.1, or 14.04.4.2), then you're running an interim HWE stack and you'll need to upgrade the HWE stack:
```
# First, run soup to ensure that all updates have been installed
sudo soup

# If soup prompts to reboot, then do so

# Now upgrade to the new HWE stack
sudo apt-get install --install-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial 
```

Our recent 14.04.5.1 ISO image already includes the 16.04 Xenial HWE stack.

### More information
For more information, please see:  

https://lists.ubuntu.com/archives/ubuntu-security-announce/2016-July/003493.html

https://wiki.ubuntu.com/Kernel/LTSEnablementStack