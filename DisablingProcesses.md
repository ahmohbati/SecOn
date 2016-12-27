#### Disabling a process ####
If you've already run Setup and want to disable a certain sensor service, you can simply stop the running service and then change the corresponding config value from `yes` to `no` to prevent it from restarting the next time the NSM scripts are run.

For example, suppose you access Bro's HTTP logs via ELSA, so you want to disable `http_agent` to prevent those HTTP logs from being duplicated into the `Sguil` database.  You would first stop the running `http_agent` service:
```
sudo nsm_sensor_ps-stop --only-http-agent
```
You would then edit `/etc/nsm/$HOSTNAME-$INTERFACE/sensor.conf` and change:
```
HTTP_AGENT_ENABLED="yes"
```
to:
```
HTTP_AGENT_ENABLED="no"
```
to prevent `http_agent` from restarting the next time the NSM scripts are run.  A quick way to do this for all `/etc/nsm/*/sensor.conf` files on one box is to use the `sed` command as follows:
```
sudo sed -i 's|HTTP_AGENT_ENABLED="yes"|HTTP_AGENT_ENABLED="no"|g' /etc/nsm/*/sensor.conf
```
<br>
#### Sguil Agent ####
If you use the Sguil client and want to remove the disabled agent from Sguil's `Agent Status` tab, then stop `sguild`, set the sensor's `active` field to `N` in the database, and then restart `sguild`:
```
# Stop sguild
sudo nsm_server_ps-stop

# Set active="N", replacing HOSTNAME-INTERFACE-INSTANCE with your actual HOSTNAME, INTERFACE, and INSTANCE
sudo mysql --defaults-file=/etc/mysql/debian.cnf -Dsecurityonion_db -e 'update sensor set active="N" where hostname="HOSTNAME-INTERFACE-INSTANCE";'

# Restart sguild
sudo nsm_server_ps-start
```
<br>
#### Disabling `Xplico`
Disable Xplico in /etc/nsm/securityonion.conf:
```
sudo sed -i 's|XPLICO_ENABLED=yes|XPLICO_ENABLED=no|g' /etc/nsm/securityonion.conf
```

(Optional) Remove Xplico:
```
sudo apt-get purge xplico
```

#### Disabling `Snorby`
1. Disable Snorby in the Apache configuration:

    ```
    sudo a2dissite snorby
    ```
    
1. Reload Apache configuration:

    ```
    sudo service apache2 reload
    ```
    
1. Prevent Snorby worker from starting on boot by setting `SNORBY_ENABLED=no` in `/etc/nsm/securityonion.conf`.
1. Comment out the output database line in all `barnyard2.conf` files on ALL sensors:

    ```
  sudo sed -i 's|output database: alert, mysql, user=root dbname=snorby host=127.0.0.1|#output database: alert, mysql, user=root dbname=snorby host=127.0.0.1|g' /etc/nsm/*/barnyard2*.conf
    ```
    
1. Restart barnyard2 on all sensors:

    ```
    sudo nsm_sensor_ps-restart --only-barnyard2
    ```
<br>
<br>

#### Disabling `OSSEC`

You can disable OSSEC as follows:
```
# Stop the running OSSEC processes 
sudo service ossec-hids-server stop

sudo update-rc.d -f ossec-hids-server disable
```
However, keep in mind that in addition to providing endpoint
visibility from OSSEC agents, the OSSEC server also monitors and
protects the Security Onion box itself.  For example, suppose that you
have an active adversary who is trying to compromise your Security
Onion box.  OSSEC may see those attempts and engage `Active Response` to
block the attacker's IP address in the host-based firewall.