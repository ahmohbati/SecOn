#### What do I need to do if I'm behind a proxy? ####

Put your proxy server settings in `/etc/environment` like this:<br>
```
export http_proxy=http://server:port
export https_proxy=https://server:port
export ftp_proxy=https://server:port
export PERL_LWP_ENV_PROXY=https://server:port
export no_proxy="localhost,127.0.0.1"
```
If you're going to run something using sudo, remember to use the "-i" option to force it to process the environment variables.  For example:<br>
```
sudo -i rule-update
```

For certain proxies (Bluecoat in particular), you may need to change from https to http in `/etc/nsm/pulledpork/pulledpork.conf`.  For more information, please see:<br>
<br>
[PulledPork Issue 154](https://code.google.com/archive/p/pulledpork/issues/154)

<a href='https://groups.google.com/d/topic/security-onion/NQ-dLLPxR6A/discussion'>https://groups.google.com/d/topic/security-onion/NQ-dLLPxR6A/discussion</a>

<a href='https://groups.google.com/d/topic/security-onion-testing/piRYj-7Ar8M/discussion'>https://groups.google.com/d/topic/security-onion-testing/piRYj-7Ar8M/discussion</a>