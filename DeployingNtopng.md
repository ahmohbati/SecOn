## Ntopng works on SO 14.04 testing

See more here:  
https://github.com/branchnetconsulting/so1404-ntopng-installer

## Ntopng does not work on SO 14.04 stable 

At this time, if you have ntopng installed according to this Wiki page on a Security Onion 12.04 system, and you upgrade Security Onion to 14.04, it will break ntopng because of a pfring version alignment issue between ntopng and SO 14.04.  The current version of pfring in SO 14.04 is 6.0.3, which is too new to work with the older ntopng version needed for SO 12.04, but too old to work with the latest stable ntopng packages from the ntop repo.  It is already on the SO roadmap to upgrade pfring in SO 14.04 to version 6.2, which is the version required by the latest stable ntopng packages from the ntop repo.  At that time I plan to test ntopng on SO 14.04 and update this Wiki page accordingly.


## Compatibility Problem of newer Ntopng releases with Security Onion

As of July 8, 2015, neither the stable nor the development version of the ntopng packages appear to be compatible with Security Onion.  This likely coincides with the release of the new 2.x branch of ntopng, which appears to be built for use with PF_RING 6.1.1 while Security Onion is using PF_RING 6.0.2.  It might be possible to build ntopng 2.x from tarball but that is outside of the scope of this article.  I recommend you just use the ntopng 1.2.2 packages for now if you can find them.

#### Introduction ####

How to install and get started with Ntopng on a Security Onion box

#### Author ####

This page was written by Kevin Branch.

#### Testing ####

This procedure was last successfully tested by Kevin on 1/30/2015 when the latest stable ntopng was at version 1.2.2, rev `8661`.  At that time, the newer nightly build revision `8884` was broken, so this article now references the stable repo instead of the nightly build repo.

#### No Support ####

Since ntopng is not an official part of Security Onion, we don't provide official support for it.

#### About the ntopng apt repository ####

Don't add that repo to your Security Onion system.  As nice as it would be to have ntopng updated as part of the "soup" process, adding the ntopng apt repository to your apt sources appears to break Security Onion because it will cause the pfring package from the ntopng repo to be installed in parallel to the Security Onion securityonion-pfring-`*` packages, which generally aren't on the same PFRING version, causing various applications to fail.

If you've already been broken by this, I believe that after removing the ntop repository from your apt sources, the following will put things back to normal:
```
apt-get purge pfring
apt-get --reinstall install securityonion-pfring-*
```

#### Are your http requests for ntop getting redirected to https? ####

Something in Security Onion appear to use HSTS to mark the SO host name for HTTPS-only use, so when you use a browser that honors HSTS -- like Chrome -- to access your ntop instance via the same host name as your other SO apps, it will redirect you to https which isn't what ntop is listening on.  The ideal solution is to enable https support in ntop, but I've not had luck with that yet.  The other options are to access ntop via the raw IP number of the SO box, or to set up an additional DNS name that points at your SO system, and use that name exclusively for reaching ntop.

#### Installation Details ####

```
# Ntopng depends on this package
apt-get install redis-server libhiredis0.10 rrdtool libnl1

# Fetch and install the latest stable build of the ntopng and ntopng-data deb packages
DEB_FILE_1=`curl -s http://www.nmon.net/apt-stable/12.04/x64/ 2>&1 | grep ntopng_ | tail -n1 | cut -d\" -f8`
DEB_FILE_2=`curl -s http://www.nmon.net/apt-stable/12.04/all/ 2>&1 | grep ntopng-data | tail -n1 | cut -d\" -f8`
wget http://www.nmon.net/apt-stable/12.04/x64/$DEB_FILE_1
wget http://www.nmon.net/apt-stable/12.04/all/$DEB_FILE_2
dpkg -i $DEB_FILE_1 
dpkg -i $DEB_FILE_2

# Make ntopng start at boot
touch /etc/ntopng/ntopng.start

# Set up an ntopng data directory
mkdir /usr/local/ntopng
chown nobody:root /usr/local/ntopng

# Edit /etc/ntopng/ntopng.conf, using the ntopng man page to figure out what options you want.
# You might start with something like this:
	--data-dir=/usr/local/ntopng
	--local-networks="192.168.0.0/16,10.0.0.0/8"
	--interface=eth1
	--dns-mode=1
	--disable-login
	--packet-filter="ip and not proto ipv6 and not ether host ff:ff:ff:ff:ff:ff and not net (224.0.0.0/8 or 239.0.0.0/8)"
	--daemon
	-G=/var/tmp/ntopng.pid
# Make sure to include at least the -G line in the above example exactly as seen, as the ntopng control script will fail without it.

# Open the ntopng web listener port in iptables
ufw allow 3000/tcp

# Manually start the service
service ntopng start

# Surf to http://NSM_HOST_NAME:3000 and try out your new ntopng installation!
```