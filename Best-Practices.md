Disable any unnecessary services.  First, Snorby should be disabled since it is now considered unmaintained:
https://github.com/Security-Onion-Solutions/security-onion/wiki/DisablingProcesses#disabling-snorby

In addition, most folks will want to disable the following services:
* prads (prads creates session data and asset data, already provided by Bro)
* pads_agent (not needed if prads is disabled)
* sancp_agent (not needed if prads is disabled)
* argus (argus creates session data, which is already provided by Bro)
* http_agent (duplicates Bro http.log into Sguil database, which may cause performance issues)

For more information, please see [Disabling Processes](DisablingProcesses#disabling-a-process).