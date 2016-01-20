#### Welcome to the Security Onion Installation Guide! ####

To install Security Onion, you're going to either install our Security Onion ISO image **or** install a standard Ubuntu 14.04 ISO image and then add our Security Onion PPA and packages.  **Please keep in mind that our PPA and packages are only compatible with Ubuntu 14.04**.

#### ALWAYS verify the checksum of ANY downloaded ISO image ####
Regardless of whether you're downloading our Security Onion ISO image or whether you're starting with an Ubuntu 14.04 ISO image, you should ALWAYS verify the checksum of the downloaded ISO image.
  * If downloading our Security Onion 14.04.3.1 ISO image, please verify the checksums here:
https://github.com/Security-Onion-Solutions/security-onion/blob/master/checksums.txt
  * If downloading an Ubuntu 14.04 ISO image, use the accompanying .md5 file.
Here are some Ubuntu instructions for verifying checksums:
https://help.ubuntu.com/community/HowToMD5SUM

#### Hardware ####
If you haven't already, please review the [Hardware](Hardware) page.

#### UEFI ####
If you have a new machine with UEFI, please see:
https://help.ubuntu.com/community/UEFI
<br>
<br>
### Choose your Installation Guide ###
We have different Installation Guides to cover various use cases.  Please choose the appropriate Installation Guide for your use case.

#### Quickly Evaluating Security Onion ####
If you just want to **quickly evaluate** Security Onion, choose one of the following.  If you're a first time user, please choose the first option.

  * [Download our Security Onion ISO image and Quickly Evaluate](QuickISOImage)

OR

  * [Quickly Evaluating Security Onion using **your preferred flavor of Ubuntu 14.04**](InstallingOnUbuntu)

#### Production Deployment ####
If you're deploying Security Onion in **production**, please see:
  * [Production Deployment](ProductionDeployment)