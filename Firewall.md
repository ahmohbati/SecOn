# UFW - Uncomplicated Firewall #
The default firewall configuration tool for Ubuntu is ufw. By default UFW is enabled on Security Onion.

## Enable/Disable ##
```
sudo ufw enable
```

```
sudo ufw disable
```
## Allow/Deny ##

**example:** allow port 9876 for Xplico
```
sudo ufw allow 9876/tcp
```
**example:** allow irc port range 6667 - 7000
```
sudo ufw allow 6667:7000
```
**example:** deny https
```
sudo ufw deny 443
```

## What Ports Are Opened/Listening ##
**example**
```
sudo ufw status
```
**example output**
```
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere
7734/tcp                   ALLOW       Anywhere
7736/tcp                   ALLOW       Anywhere
443/tcp                    ALLOW       Anywhere
```

## Setup defaults to only allowing port 22 (ssh)
As of securityonion-setup - 20120912-0ubuntu0securityonion201, Setup now defaults to only allowing port 22 (ssh).  There is a note at the end of Setup that tells you this and lets you know that if you need to allow connections on other ports, you can run the new `so-allow` utility.  

When you run Setup on a sensor-only installation, it will ssh to the master server and add new firewall rules to the master server to allow the sensor to connect on ports 22,4505,4506,7736.  

If you need to open ports for OSSEC agents, syslog devices, or analyst VMs, you can run `so-allow` and it will walk you through this process.

## Older firewall documentation has been moved
If you're still running a version of Setup older than securityonion-setup - 20120912-0ubuntu0securityonion201, then you can reference the [original firewall documentation](firewall-old).

## More Info ##
For more info you can visit the UFW documentation [site](https://help.ubuntu.com/community/UFW)

Note: [Gufw](https://help.ubuntu.com/community/Gufw) is a GUI front end for the ufw.