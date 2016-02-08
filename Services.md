Services are controlled by the NSM scripts.

Check status of all services:
```
sudo service nsm status
```

Start all services:
```
sudo service nsm start
```

Stop all services:
```
sudo service nsm stop
```

Restart all services:
```
sudo service nsm restart
```

# Server services
Check status of sguild (Sguil server):
```
sudo nsm_server-ps-status
```

Start sguild:
```
sudo nsm_server_ps-start
```

Stop sguild:
```
sudo nsm_server_ps-stop
```

Restart sguild:
```
sudo nsm_server_ps-restart
```

# Sensor services
Sensor services are controlled with nsm_sensor_ps-*.

List of controlled services:
```
sudo nsm_sensor_ps-* -?

```

The following examples are for Bro, but you could substitute whatever sensor service you're trying to control.

Check status of Bro:
```
sudo nsm_sensor_ps-status --only-bro
```

Start Bro:
```
sudo nsm_sensor_ps-start --only-bro
```

Stop Bro:
```
sudo nsm_sensor_ps-stop --only-bro
```

Restart Bro:
```
sudo nsm_sensor_ps-restart --only-bro
```
