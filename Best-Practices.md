Disable any unnecessary services.  In particular, most folks will want to disable the following services:
* Snorby (Snorby is now considered unmaintained)
* prads (prads creates session data and asset data, already provided by Bro)
* pads_agent (not needed if prads is disabled)
* sancp_agent (not needed if prads is disabled)
* argus (argus creates session data, which is already provided by Bro)
* http_agent (duplicates Bro http.log into Sguil database, which may cause performance issues)

For more information, please see [Disabling Processes](DisablingProcesses).