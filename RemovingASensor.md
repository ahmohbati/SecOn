There may come a time when you need to disable a sensor interface, delete a sensor's configuration, or get rid of an entire sensor and its data altogether.  The steps below outline what is required to accomplish each objective. 

#### Disable sensor interface
* To disable a sensor interface, simply comment out the interface in `/etc/nsm/sensortab` and in `/opt/bro/etc/node.cfg` on the sensor box for which you wish to disable the interface.  
* Restart NSM service(s) (`sudo service nsm restart`) and/or reboot to ensure changes have taken effect.

#### Delete sensor configuration
* To delete the configuration for a sensor, run `/usr/sbin/nsm_sensor_del` on the sensor box for which you wish to delete the configuration.

#### Wipe sensor configuration and data
* To completely wipe sensor configuration and data, run `/usr/bin/sosetup` on the sensor box for which you wish to wipe the data and configuration.

#### Remove sensor reference from master server

* On the master server, edit `/etc/elsa_web.conf`, remove the sensor from the `peers` section, then restart Apache (`sudo service apache2 restart`). 

* In MySQL database securityonion_db, edit sensor table (you can simply set 
 active='N'), then restart sguild. 
  * Stop sguild<br> `sudo nsm_server_ps-stop` 
  * Show sensor entries<br> `sudo mysql --defaults-file=/etc/mysql/debian.cnf -Dsecurityonion_db -e 'select * from sensor';`
  * Set sensor as inactive<br> 
  `sudo mysql --defaults-file=/etc/mysql/debian.cnf -Dsecurityonion_db -e "update sensor set active='N' where sid in (<SID1>,<SID2>)";`
  * Start sguild<br> `sudo nsm_server_ps-start `


* If running salt, remove the sensor from `/opt/onionsalt/salt/top.sls`.