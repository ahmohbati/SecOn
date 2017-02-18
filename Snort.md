We compile Snort with PF_RING to allow you to spin up multiple instances to handle more traffic.

Configuration:
/etc/nsm/HOSTNAME-INTERFACE/snort.conf

Log file:
/var/log/nsm/snortu-x.log (where x represents the number of PF_RING instances)

For more information about Snort, please see:
http://snort.org