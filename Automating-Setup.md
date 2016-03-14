You can automate the Setup process using `sosetup.conf`.

Copy the example file to your home directory:  
```
cp /usr/share/securityonion/sosetup.conf ~
```

Edit your new `sosetup.conf` using `nano` or your favorite text editor:  
```
nano ~/sosetup.conf
```

Run Setup with the -f switch and the path to this file:  
```
sudo sosetup -f ~/sosetup.conf
```

As of securityonion-setup - 20120912-0ubuntu0securityonion201, sosetup now supports a -w switch that allows you to answer the standard Setup questions and have it write out your custom sosetup.conf:  
http://blog.securityonion.net/2016/03/securityonion-setup-20120912.html  