#### Setup ####

If you have multiple CPU cores, Setup will automatically ask you how many PF\_RING instances you'd like for Snort/Suricata (IDS engine processes) and Bro and will tell you how to adjust after the fact.  As of securityonion-setup - 20120912-0ubuntu0securityonion201, Setup should analyze your system and recommend a certain number of PF_RING instances:  
http://blog.securityonion.net/2016/03/securityonion-setup-20120912.html

#### Tuning

If you want to change the number of PF\_RING instances after running Setup, you can do the following.

#### Snort/Suricata

  * Stop sensor processes:
```
sudo nsm_sensor_ps-stop
```
  * Edit `/etc/nsm/$HOSTNAME-$INTERFACE/sensor.conf` and change the `IDS_LB_PROCS` variable to desired number of cores.
  * Start sensor processes:
```
sudo nsm_sensor_ps-start
```

If running Snort, the script automatically spawns $IDS\_LB\_PROCS instances
of Snort (using PF\_RING), barnyard2, and snort\_agent.<br>
If running Suricata, the script automatically copies $IDS_LB_PROCS into<br>
suricata.yaml and then Suricata spins up the PF_RING instances itself.<br>
<br>
#### Bro
For Bro, you would do the following:<br>
<ul><li>Stop bro:<br>
<pre><code>sudo nsm_sensor_ps-stop --only-bro<br>
</code></pre>
</li><li>Edit <code>/opt/bro/etc/node.cfg</code> and change the <code>lb_procs</code> variable to the desired number of cores.<br>
</li><li>Start bro:<br>
<pre><code>sudo nsm_sensor_ps-start --only-bro<br>
</code></pre></li></ul>

#### Slots
If you've already run Setup and want to modify min_num_slots, you can manually create/edit <code>/etc/modprobe.d/pf_ring.conf</code>.  

For example, to increase min_num_slots to 65534, do the following:<br><br>
<code>echo "options pf_ring transparent_mode=0 min_num_slots=65534" | sudo tee /etc/modprobe.d/pf_ring.conf</code>
<br><br>After creating/editing <code>/etc/modprobe.d/pf_ring.conf</code>, you'll need to reload the PF_RING module as follows (or just reboot):<br><br>
<code>sudo nsm_sensor_ps-stop</code><br>
<code>sudo rmmod pf_ring</code><br>
<code>sudo nsm_sensor_ps-start</code>

#### Updating
Please see the [Upgrade](Upgrade) page for notes on updating the PF_RING kernel module.
