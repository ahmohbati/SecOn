
At Security Onion Conference 2016, Eric Conrad shared some IDS rules for detecting unusual ICMP echo/replies and identifying C2 channels that may utilize ICMP tunneling for covert communication.  

We can add these rules to `/etc/nsm/rules/local.rules` so that we can gain better insight into ICMP echoes or replies over a certain size, containing particularly suspicious content, etc.

You can find the rules and Eric's presentation here:<br/>
http://www.ericconrad.com/2016/09/c2-phone-home-leveraging-securityonion.html