#### Adding proxy settings to /etc/environment

Put your proxy server settings in `/etc/environment` like this:<br>
```
export http_proxy=http://server:port
export https_proxy=https://server:port
export ftp_proxy=https://server:port
export PERL_LWP_ENV_PROXY=https://server:port
export no_proxy="localhost,127.0.0.1"
```

#### sudo
If you're going to run something using sudo, remember to use the "-i" option to force it to process the environment variables.  For example:<br>
```
sudo -i rule-update
```

#### PulledPork
As of [PulledPork 0.7.2](http://blog.securityonion.net/2017/01/pulledpork-rule-update-and-several.html), you may need to pass the -W option to Pulledpork:
```
-W Where you want to work around the issue where some implementations of LWP do not work with pulledpork's proxy configuration.
```

If you find that you need this option, you can add the following to /etc/nsm/securityonion.conf:
```
PULLEDPORK_OPTIONS="-W"
```

For older versions of PulledPork and certain proxies (Bluecoat in particular), you may need to change from https to http in `/etc/nsm/pulledpork/pulledpork.conf`.  For more information, please see:<br>
<br>
[PulledPork Issue 154](https://code.google.com/archive/p/pulledpork/issues/154)

<a href='https://groups.google.com/d/topic/security-onion/NQ-dLLPxR6A/discussion'>https://groups.google.com/d/topic/security-onion/NQ-dLLPxR6A/discussion</a>

<a href='https://groups.google.com/d/topic/security-onion-testing/piRYj-7Ar8M/discussion'>https://groups.google.com/d/topic/security-onion-testing/piRYj-7Ar8M/discussion</a>