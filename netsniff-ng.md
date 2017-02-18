### What is netsniff-ng?
From http://netsniff-ng.org:
> netsniff-ng is a free Linux networking toolkit, a Swiss army knife for your daily Linux network plumbing if you will.  Its gain of performance is reached by zero-copy mechanisms, so that on packet reception and transmission the kernel does not need to copy packets from kernel space to user space and vice versa.

### What does Security Onion use netsniff-ng for?
Security Onion uses netsniff-ng to collect full packet capture.

### Where does netsniff-ng write to?
netsniff-ng writes full packet capture in the form of pcap files to:
/nsm/sensor_data/HOSTNAME-INTERFACE/dailylogs/YYYY-MM-DD/
(where HOSTNAME is your actual hostname, INTERFACE is your actual sniffing interface, and YYYY-MM-DD is the year, month, and date the pcap was recorded)

### Where can I find the netsniff-ng log file for troubleshooting? 
/var/log/nsm/HOSTNAME-INTERFACE/netsniff-ng.log  
(where HOSTNAME is your actual hostname and INTERFACE is your actual sniffing interface)

### Where can I find more information about netsniff-ng?
For more information about netsniff-ng, please see:  
http://netsniff-ng.org/