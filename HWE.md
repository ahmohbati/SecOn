### Introduction
HWE stands for Hardware Enablement and is Ubuntu's term for kernel and graphics driver support.  Depending on which HWE stack you're running, you may need to upgrade it.  

### Security Onion 14.04 ISO images and HWE stacks
If you installed your system using our older Security Onion 14.04 ISO images (14.04.3.1, 14.04.4.4.1, or 14.04.4.2), then you're running an interim HWE stack and you'll need to upgrade the HWE stack.  

If you installed using our Security Onion 14.04.5.1 (or newer) ISO image, then it already includes the 16.04 Xenial HWE stack and should not require any HWE upgrades.

### Install updates first
Some older versions may not have the hwe-support-status tool that we're going to use in the next step, so our first step is to install all updates using [soup](Upgrade):
```
sudo soup
```
If soup prompts to reboot, please do so.

### Check HWE Status
Now that all updates have been installed, run the `hwe-support-status` tool to see if your HWE stack is supported:
```
sudo hwe-support-status
```

If it says `Your Hardware Enablement Stack (HWE) is supported until April 2019`, then no further action is required and you can ignore the rest of the page.  If you got something other than that, then please continue reading!

### Upgrade HWE
If you're running Security Onion 14.04 and you get a WARNING that security updates have ended, you may need to upgrade your HWE stack using the "Ubuntu 14.04 LTS - Trusty Tahr" instructions here:  
https://wiki.ubuntu.com/Kernel/LTSEnablementStack

### Example
For example, if you installed your system using our older Security Onion 14.04 ISO images (14.04.3.1, 14.04.4.4.1, or 14.04.4.2), then you're running an interim HWE stack and you'll need to upgrade the HWE stack as follows:
```
# First, run soup to ensure that all updates have been installed
sudo soup

# If soup prompts to reboot, then do so

# Next, run hwe-support-status to check the status of your HWE stack
sudo hwe-support-status

# If hwe-support-status asks you to upgrade to a new HWE stack, then do the following:
sudo apt-get install --install-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial 
```

### More information
For more information, please see:  

https://lists.ubuntu.com/archives/ubuntu-security-announce/2016-July/003493.html

https://wiki.ubuntu.com/Kernel/LTSEnablementStack