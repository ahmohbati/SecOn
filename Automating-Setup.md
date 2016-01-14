You can automate the Setup process using sosetup.conf

Copy the example file to your home directory:
```cp /usr/share/securityonion/sosetup.conf ~```

Edit your new sosetup.conf using nano or your favorite text editor:
```nano ~/sosetup.conf```

Run Setup with the -f switch and the path to this file:
```sudo sosetup -f ~/sosetup.conf```
