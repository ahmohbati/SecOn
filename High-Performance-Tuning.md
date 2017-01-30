First, make sure you're following [Best Practices](Best-Practices).

Disable GUI:  
http://askubuntu.com/questions/16371/how-do-i-disable-x-at-boot-time-so-that-the-system-boots-in-text-mode

Disable Bluetooth:
```
sudo sh -c "echo manual > /etc/init/bluetooth.override"
```

Disable Avahi:
```
sudo sh -c "echo manual > /etc/init/avahi-daemon.override"
```

Disable any other services that you may not need like cupsd, cups-browsed, etc.

Consider adopting some of the suggestions from here:  
https://github.com/pevma/SEPTun