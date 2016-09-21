HWE stands for Hardware Enablement and is Ubuntu's term for kernel and graphics driver support.

Check to see if your HWE stack is supported:
```
sudo hwe-support-status
```

If you're running Security Onion 14.04 and you get a WARNING that security updates have ended, you may need to upgrade your HWE stack using the "Ubuntu 14.04 LTS - Trusty Tahr" instructions here:  
https://wiki.ubuntu.com/Kernel/LTSEnablementStack

For example, if you installed your system using our original Security Onion 14.04 ISO images (14.04.3.1, 14.04.4.4.1, or 14.04.4.2), then you're running an interim HWE stack and you'll need to upgrade the HWE stack:
```
sudo apt-get install --install-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial 
```