### Description
From http://www.xplico.org/about:
> The goal of Xplico is extract from an internet traffic capture the applications data contained.
For example, from a pcap file Xplico extracts each email (POP, IMAP, and SMTP protocols), all HTTP contents, each VoIP call (SIP), FTP, TFTP, and so on. Xplico isn’t a network protocol analyzer. Xplico is an open source Network Forensic Analysis Tool (NFAT).

### Enabling Xplico
Xplico is enabled automatically if you choose Evaluation Mode.  Production Mode disables Xplico.  This is controlled by the `XPLICO_ENABLED` setting in `/etc/nsm/securityonion.conf`.

### Logging In
From http://wiki.xplico.org/doku.php?id=interface:
> The default username and password are:  
username: xplico  
password: xplico  
>  
The default admin username and password are:  
username: admin  
password: xplico

### More Information
For more information, please see:  
http://www.xplico.org/