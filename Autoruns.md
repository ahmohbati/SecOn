### Description
From https://technet.microsoft.com/en-us/sysinternals/bb963902.aspx:
> This utility, which has the most comprehensive knowledge of auto-starting locations of any startup monitor, shows you what programs are configured to run during system bootup or login, and when you start various built-in Windows applications like Internet Explorer, Explorer and media players. These programs and drivers include ones in your startup folder, Run, RunOnce, and other Registry keys. Autoruns reports Explorer shell extensions, toolbars, browser helper objects, Winlogon notifications, auto-start services, and much more. Autoruns goes way beyond other autostart utilities.

### Integration
Josh Brower developed a great project called Pertinax to normalize autoruns data and integrate it into Security Onion:  
https://github.com/defensivedepth/Pertinax/wiki/Introduction

Josh's syslog-ng patterns were merged into Security Onion here:  
http://blog.securityonion.net/2016/08/new-elsa-packages-resolve-several-issues.html

Execute autoruns and ar-normalize.ps1 as shown here:  
https://github.com/defensivedepth/Pertinax/wiki/Reference%20Architecture

### Downloads
Download Autoruns here:  
https://download.sysinternals.com/files/Autoruns.zip

Download ar-normalize.ps1 here:  
https://raw.githubusercontent.com/defensivedepth/Pertinax/master/normalize/ar-normalize.ps1
