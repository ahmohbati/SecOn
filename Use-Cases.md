Security Onion is designed for many different use cases!  Here are just a few examples.

### Classroom
Evaluation Mode is ideal for classroom or lab environments.

Install Security Onion.  Run Setup and configure network interfaces.  Reboot, run Setup, and then choose Evaluation Mode.  

For more information, please see:  
https://github.com/Security-Onion-Solutions/security-onion/wiki/QuickISOImage

### Production Server - Standalone
Install Security Onion.  Run Setup and configure network interfaces.  Reboot, run Setup, choose Production Mode, and then choose Standalone.  

For more information, please see:  
https://github.com/Security-Onion-Solutions/security-onion/wiki/ProductionDeployment

### Production Server - Distributed Deployment
Install Security Onion on the master server box.  Run Setup and configure network interfaces.  Reboot, run Setup, choose Production Mode, and then choose Master.
Install Security Onion on one or more sensor boxes and then on each one:  run Setup, configure network interfaces, reboot, run Setup choose Production Mode, and then choose Sensor.

For more information, please see:  
https://github.com/Security-Onion-Solutions/security-onion/wiki/ProductionDeployment

### Analyst VM
Install Security Onion in a VM on your local desktop or laptop.  Do NOT run Setup.  Launch the Sguil client and connect to sguild on your Production Master Server.  Launch the web browser and connect to Squert or ELSA on your Production Master Server.  

For more information, please see:  
https://github.com/Security-Onion-Solutions/security-onion/wiki/ConnectingtoSguil#directly-connecting-to-sguild-remotely

### Sensor sending logs to SIEM
Install Security Onion on a sensor box and then configure it to send logs to your SIEM.

For more information, please see:  
[Sending logs to SIEM](ThirdPartyIntegration)