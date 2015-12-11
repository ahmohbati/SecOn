Security Onion consists of over 70 Ubuntu packages in a Launchpad PPA.  You can install these packages individually or you can install one or more metapackages (groups of packages) depending on what functionality you need.

#### Metapackages ####

  * securityonion-client (about 525MB)  
Sguil client, Wireshark, NetworkMiner, etc.  
```sudo apt-get install securityonion-client```

  * securityonion-sensor (about 135MB)  
Snort, Suricata, Bro, netsniff-ng, Sguil agents, etc.  
```sudo apt-get install securityonion-sensor```

  * securityonion-server (about 265MB)  
Sguil server, Squert, CapMe, etc.  
```sudo apt-get install securityonion-server```

  * securityonion-elsa and securityonion-elsa-extras (about 268MB)  
ELSA web interface, log node, parsers/pattterns, syslog-ng, etc.  
Since this metapackage depends on syslog-ng (which conflicts with rsyslog), you may need to specifically include syslog-ng and syslog-ng core in your install line like:  
```sudo apt-get install securityonion-elsa securityonion-elsa-extras syslog-ng syslog-ng-core```

  * securityonion-all (about 912MB)
all of the above  
```sudo apt-get install securityonion-all syslog-ng syslog-ng-core```

  * securityonion-iso (new in Security Onion 14.04) (about 1004MB)
all of the above plus bridge-utils, byobu, foremost, securityonion-onionsalt, securityonion-samples-markofu, securityonion-samples-mta, securityonion-samples-shellshock, xfsprogs, xplico  
```sudo apt-get install securityonion-iso syslog-ng syslog-ng-core```