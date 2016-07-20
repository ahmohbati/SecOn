If you're monitoring VLAN tagged traffic with Snort or Suricata, you may need to modify your configuration to avoid inconsistent alerting.  Here are some things to consider.  As of securityonion-setup - 20120912-0ubuntu0securityonion222, Setup will automatically increase interface MTU and Snort/Suricata snaplen to account for VLAN tags:  
http://blog.securityonion.net/2016/07/securityonion-setup-20120912.html

### Snort
Snort's default Snap Length is 1514.  To allow for VLAN tags, you should increase this to 1518 by setting the following option in your Snort configuration file `/etc/nsm/HOSTNAME-INTERFACE/snort.conf`:
```
config snaplen: 1518
```

Restart Snort:
```
sudo nsm_sensor_ps-restart --only-snort-alert
```
Test to ensure that you're now receiving consistent alerting.

### Suricata
When Suricata receives packets from PF_RING, it sets the Snap Length (Bucket Len) to 1516 by default (the default MTU of the sniffing interface 1500 plus 16).  To increase Suricata's Snap Length to 1518, increase the MTU of your sniffing interface to 1502 by adding the following line to the sniffing interface section of your network interface config file `/etc/network/interfaces`:
```
    mtu 1502
```
Then bounce the interface as follows (replacing eth1 with your actual sniffing interface):
```
sudo ifdown eth1
sudo ifup eth1
```

If you have inconsistent VLAN tags (for example, VLAN tags in one direction but not the other), then you may also need to set the following option in your Suricata configuration file `/etc/nsm/HOSTNAME-INTERFACE/suricata.yaml`:
```
vlan:
  use-for-tracking: false
```

Restart Suricata:
```
sudo nsm_sensor_ps-restart --only-snort-alert
```
Test to ensure that you're now receiving consistent alerting.