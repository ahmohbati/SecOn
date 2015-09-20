Disable any unnecessary services.  First, Snorby should be disabled since it is now considered unmaintained:
https://github.com/Security-Onion-Solutions/security-onion/wiki/DisablingProcesses#disabling-snorby

In addition, most folks will want to disable the following services:
* prads (prads creates session data and asset data, already provided by Bro)
* pads_agent (not needed if prads is disabled)
* sancp_agent (not needed if prads is disabled)
* argus (argus creates session data, which is already provided by Bro)
* http_agent (duplicates Bro http.log into Sguil database, which may cause performance issues)

To do so:

    sudo nsm_sensor_ps-stop --only-http-agent
    sudo nsm_sensor_ps-stop --only-prads
    sudo nsm_sensor_ps-stop --only-pads-agent
    sudo nsm_sensor_ps-stop --only-sancp-agent
    sudo nsm_sensor_ps-stop --only-argus
 
    sudo sed -i 's|HTTP_AGENT_ENABLED="yes"|HTTP_AGENT_ENABLED="no"|g' /etc/nsm/*/sensor.conf
    sudo sed -i 's|PRADS_ENABLED="yes"|PRADS_ENABLED="no"|g' /etc/nsm/*/sensor.conf
    sudo sed -i 's|PADS_AGENT_ENABLED="yes"|PADS_AGENT_ENABLED="no"|g' /etc/nsm/*/sensor.conf
    sudo sed -i 's|SANCP_AGENT_ENABLED="yes"|SANCP_AGENT_ENABLED="no"|g' /etc/nsm/*/sensor.conf
    sudo sed -i 's|ARGUS_ENABLED="yes"|ARGUS_ENABLED="no"|g' /etc/nsm/*/sensor.conf

For more information, please see [Disabling Processes](DisablingProcesses#disabling-a-process).