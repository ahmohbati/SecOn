#### Setup ####

If you have multiple CPU cores, Setup will automatically ask you how many PF\_RING instances you'd like for Snort/Suricata (IDS engine processes) and Bro and will tell you how to adjust after the fact.  As of securityonion-setup - 20120912-0ubuntu0securityonion201, Setup should analyze your system and recommend a certain number of PF_RING instances:  
http://blog.securityonion.net/2016/03/securityonion-setup-20120912.html

#### Tuning

If you want to change the number of PF\_RING instances after running Setup, you can do the following.

#### Snort/Suricata

  * Stop sensor processes:<br>
`sudo nsm_sensor_ps-stop`
  * Edit `/etc/nsm/$HOSTNAME-$INTERFACE/sensor.conf` and change the `IDS_LB_PROCS` variable to desired number of cores.
  * Start sensor processes:<br>
`sudo nsm_sensor_ps-start`

If running Snort, the script automatically spawns $IDS\_LB\_PROCS instances of Snort (using PF\_RING), barnyard2, and snort\_agent.

If running Suricata, the script automatically copies $IDS_LB_PROCS into suricata.yaml and then Suricata spins up the PF_RING instances itself.

#### Bro
For Bro, you would do the following:<br>
* Stop bro:<br>
`sudo nsm_sensor_ps-stop --only-bro`
* Edit <code>/opt/bro/etc/node.cfg</code> and change the <code>lb_procs</code> variable to the desired number of cores.<br>
* Start bro:<br>
`sudo nsm_sensor_ps-start --only-bro`

#### Slots
If you've already run Setup and want to modify min_num_slots, you can manually create/edit <code>/etc/modprobe.d/pf_ring.conf</code>.  

For example, to increase min_num_slots to 65534, do the following:<br>
`echo "options pf_ring transparent_mode=0 min_num_slots=65534" | sudo tee /etc/modprobe.d/pf_ring.conf`

After creating/editing `/etc/modprobe.d/pf_ring.conf`, you'll need to reload the PF_RING module as follows (or just reboot):<br>
`sudo nsm_sensor_ps-stop`
`sudo rmmod pf_ring`<br>
`sudo nsm_sensor_ps-start`

#### Updating
Please see the [Upgrade](Upgrade) page for notes on updating the PF_RING kernel module.
