* Developed by Paul Halliday:  
http://www.squertproject.org/

* PHP web interface to Sguil database

* Squert authenticates against the Sguil user database, so you should be able to login to Squert using the same username/password you use to login to Sguil

* Gives you access to the following data types:
  * NIDS alerts
  * HIDS alerts
  * Asset data from PRADS (if PRADS and pads_agent are enabled)
  * HTTP logs from Bro (if http_agent is enabled)

* Can natively pivot to TCP transcripts from full packet capture

* Can also pivot to ELSA to query Bro logs