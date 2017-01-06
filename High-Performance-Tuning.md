First, make sure you're following [Best Practices](Best-Practices).

Disable GUI:
http://askubuntu.com/questions/16371/how-do-i-disable-x-at-boot-time-so-that-the-system-boots-in-text-mode

Disable Bluetooth:
```
sudo sh -c "echo 'manual' > /etc/init/bluetooth.override"
```

Consider adopting some of the suggestions from here:  
https://github.com/pevma/SEPTun