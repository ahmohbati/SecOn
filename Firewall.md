## Setup defaults to only allowing port 22 (ssh)
As of securityonion-setup - 20120912-0ubuntu0securityonion201, Setup now defaults to locking down the local `ufw` firewall to only allowing port 22 (ssh).  There is a note at the end of Setup that tells you this and lets you know that if you need to allow connections on other ports, you can run the new `so-allow` utility.  

When you run Setup on a sensor-only installation, it will ssh to the master server and add new firewall rules to the master server to allow the sensor to connect on ports 22,4505,4506,7736.  

If you need to open ports for OSSEC agents, syslog devices, or analyst VMs, you can run `so-allow` and it will walk you through this process.  `so-allow` also provides an option to add firewall rules for sensors although you shouldn't need this under normal circumstances since they should automatically add their own rules as described above.

## Older firewall documentation has been moved
If you're still running a version of Setup older than securityonion-setup - 20120912-0ubuntu0securityonion201, then you can reference the [original firewall documentation](firewall-old).