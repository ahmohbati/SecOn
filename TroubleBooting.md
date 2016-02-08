#### Why won't the ISO image boot on my machine? ####
  * Did you verify the checksum of the downloaded ISO as described on the [Installation](Installation) page?
  * Does your machine support 64-bit?  (If you're trying to run a 64-bit VM, then your 64-bit processor must support virtualization and virtualization must be enabled in the BIOS.)  If not, then you'll need to obtain a 64-bit machine to use our 64-bit ISO image (recommended) or use your 32-bit machine by installing Ubuntu 14.04 32-bit and adding our PPA and packages as described on the [Installation](Installation) page.
  * If you think your machine does support 64-bit, but you're still having problems with our 64-bit ISO image, try downloading the Ubuntu 14.04 64-bit ISO image and seeing if it runs.  If it doesn't, then you should verify your 64-bit compatibility.
  * If the ISO image boots, but the Live Desktop doesn't appear properly, it may be an issue with your video card.  Try the `nomodeset` option on the boot menu:<br>
<a href='http://blog.securityonion.net/2014/02/security-onion-12044-iso-image-now.html'>http://blog.securityonion.net/2014/02/security-onion-12044-iso-image-now.html</a><br>
<a href='https://groups.google.com/d/topic/security-onion/UKE5-dqybQ4/discussion'>https://groups.google.com/d/topic/security-onion/UKE5-dqybQ4/discussion</a><br>
<a href='https://groups.google.com/d/topic/security-onion/51JZWXZfBho/discussion'>https://groups.google.com/d/topic/security-onion/51JZWXZfBho/discussion</a><br>
<br>
If that works but you are left with low resolution and you have an nvidia graphics chipset, you can do the following AFTER installation:<br>
<pre><code>sudo apt-get remove nvidia-173<br>
sudo apt-get remove nvidia-96<br>
sudo apt-get install nvidia-current<br>
</code></pre>