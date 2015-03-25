Please note that this is all subject to change!
  * January 2015
    * ~~[Issue 655](/dougburks/security-onion/issues/655): Suricata 2.0.5~~
    * [Issue 658](https://github.com/dougburks/security-onion/issues/658): NSM: fix umask on Snort unified2 output
    * [Issue 548](https://github.com/dougburks/security-onion/issues/548): NSM: run barnyard2 as non-root user
    * [Issue 649](https://github.com/dougburks/security-onion/issues/649): nsm\_all\_del\_quick: check for /etc/nsm/servertab and /etc/nsm/sensortab before trying to read
    * [Issue 598](https://github.com/dougburks/security-onion/issues/598): so-snorby-wipe
    * [Issue 610](https://github.com/dougburks/security-onion/issues/610): NSM: ossec\_agent alert level should be configurable
    * [Issue 660](https://github.com/dougburks/security-onion/issues/660): Setup: add OSSEC\_AGENT\_LEVEL to /etc/nsm/securityonion.conf
    * [Issue 656](https://github.com/dougburks/security-onion/issues/656): ELSA: update parser for bro\_conn to parse country code
    * [Issue 659](https://github.com/dougburks/security-onion/issues/659): securityonion-web-page: add ELSA query for bro\_conn groupby:resp\_country\_code
    * [Issue 667](https://github.com/dougburks/security-onion/issues/667): New packages for shellshock and malware-traffic-analysis samples
    * [Issue 673](https://github.com/dougburks/security-onion/issues/673): Suricata 2.0.6
    * [Issue 642](https://github.com/dougburks/security-onion/issues/642): Update Salt packages/scripts to 2014.7.0
    * [Issue 619](https://github.com/dougburks/security-onion/issues/619): Onionsalt: backup /opt/onionsalt/pillar/top.sls
    * [Issue 661](https://github.com/dougburks/security-onion/issues/661): Onionsalt: replicate /usr/local/lib/snort\_dynamicrules/
    * [Issue 672](https://github.com/dougburks/security-onion/issues/672): sguil-db-purge: check for UNCAT\_MAX
    * [Issue 663](https://github.com/dougburks/security-onion/issues/663): sosetup: sosetup.conf SGUIL\_CLIENT\_PASSWORD\_1 should say Sguil/Squert/ELSA/Snorby
    * [Issue 664](https://github.com/dougburks/security-onion/issues/664): sosetup: run Bro as non-root user
    * [Issue 666](https://github.com/dougburks/security-onion/issues/666): sostat: run Bro as non-root user
    * [Issue 665](https://github.com/dougburks/security-onion/issues/665): NSM: run Bro as non-root user
    * [Issue 676](https://github.com/dougburks/security-onion/issues/676): NSM: run Sguil as non-root user
    * [Issue 671](https://github.com/dougburks/security-onion/issues/671): NSM: /etc/cron.d/sensor-clean needs 2>&1
  * February 2015
    * [Issue 668](https://github.com/dougburks/security-onion/issues/668): ELSA: pdbtool errors
    * [Issue 669](https://github.com/dougburks/security-onion/issues/669): ELSA: update parsers for Bro DNS and BIND
    * [Issue 670](https://github.com/dougburks/security-onion/issues/670): securityonion-web-page: add queries for updated bro\_dns parser
    * [Issue 685](https://github.com/dougburks/security-onion/issues/685): securityonion-web-page: update links
    * [Issue 684](https://github.com/dougburks/security-onion/issues/684): NSM: nsm\_server\_ps-start needs to create /var/log/sguild/ if it doesn't already exist
    * [Issue 686](https://github.com/dougburks/security-onion/issues/686): NSM: nsm\_server\_ps-start needs to set permissions on /var/log/nsm/so-elsa/ properly
    * [Issue 687](https://github.com/dougburks/security-onion/issues/687): NSM: nsm\_sensor\_ps-start should set permissions on /var/log/nsm/ properly
    * [Issue 689](https://github.com/dougburks/security-onion/issues/689): NSM: add USE\_DNS option to ossec\_agent.conf
    * [Issue 688](https://github.com/dougburks/security-onion/issues/688): ossec\_agent: add option to disable DNS lookups
    * [Issue 680](https://github.com/dougburks/security-onion/issues/680): Bro 2.3.2
    * [Issue 683](https://github.com/dougburks/security-onion/issues/683): securityonion-et-rules: update for new ISO
    * [Issue 632](https://github.com/dougburks/security-onion/issues/632): ISO: add bridge-utils
    * [Issue 601](https://github.com/dougburks/security-onion/issues/601): ISO: add foremost
    * [Issue 614](https://github.com/dougburks/security-onion/issues/614): ISO: add securityonion-samples-shellshock
    * [Issue 662](https://github.com/dougburks/security-onion/issues/662): ISO: add securityonion-samples-mta
    * [Issue 675](https://github.com/dougburks/security-onion/issues/675): ISO: add xfsprogs
    * [Issue 602](https://github.com/dougburks/security-onion/issues/602): 12.04.5.1 ISO image
  * March 2015
    * [Issue 695](https://github.com/dougburks/security-onion/issues/695): Suricata 2.0.7
    * [Issue 696](https://github.com/dougburks/security-onion/issues/696): ELSA custom menu
    * [Issue 691](https://github.com/dougburks/security-onion/issues/691): NSM: chown -R $BRO\_USER:$BRO\_GROUP /nsm/bro >/dev/null 2>&1
    * [Issue 698](https://github.com/dougburks/security-onion/issues/698): NSM: nsm\_server\_del line 170 echo\_msg 0 "Deleting server: $SERVER\_NAME"
    * [Issue 699](https://github.com/dougburks/security-onion/issues/699): NSM: Bro node.cfg host=localhost
    * [Issue 700](https://github.com/dougburks/security-onion/issues/700): Setup: Bro node.cfg host=localhost
    * [Issue 702](https://github.com/dougburks/security-onion/issues/702): Snort 2.9.7.2
    * [Issue 703](https://github.com/dougburks/security-onion/issues/703): Move from Google Code to Github
  * April 2015
    * [Issue 705](https://github.com/dougburks/security-onion/issues/705): ossec\_agent: improvements from Brian Kellogg
    * [Issue 681](https://github.com/dougburks/security-onion/issues/681): rule-update: wipe snort\_dynamicrules directory on sensor
    * [Issue 677](https://github.com/dougburks/security-onion/issues/677): rule-update: create /usr/local/lib/snort\_dynamicrules/ if it doesn't already exist
    * [Issue 678](https://github.com/dougburks/security-onion/issues/678): rule-update: /etc/cron.d/rule-update should have 2>&1
    * [Issue 697](https://github.com/dougburks/security-onion/issues/697): rule-update: log snorby reference table update to barnyard2-snorby.log
    * [Issue 682](https://github.com/dougburks/security-onion/issues/682): rule-update: update Snorby signature\_lookup
    * [Issue 679](https://github.com/dougburks/security-onion/issues/679): rule-update: /etc/cron.d/rule-update should run pulledpork as unprivileged user
    * [Issue 690](https://github.com/dougburks/security-onion/issues/690): http\_agent: ---disable-inotify
    * [Issue 615](https://github.com/dougburks/security-onion/issues/615): NSM: add "exit $RET" where necessary
    * [Issue 392](https://github.com/dougburks/security-onion/issues/392): Patch for lib-nsm-common-utils from Mark Seiden
    * [Issue 588](https://github.com/dougburks/security-onion/issues/588): NSM: purge old OSSEC logs
    * [Issue 561](https://github.com/dougburks/security-onion/issues/561): nsm\_server\_backup-config should check FORCE\_YES
    * [Issue 523](https://github.com/dougburks/security-onion/issues/523): sensor-clean: add option to skip removal of bro or argus logs
    * [Issue 534](https://github.com/dougburks/security-onion/issues/534): NSM: Patches for adding PCAP snap length for Netsniff-NG
    * [Issue 645](https://github.com/dougburks/security-onion/issues/645): NSM scripts don't check if a sensor is disabled before performing operations when a --sensor-name= is specified
    * [Issue 652](https://github.com/dougburks/security-onion/issues/652): NSM: barnyard sending blank interface to ELSA
    * [Issue 653](https://github.com/dougburks/security-onion/issues/653): NSM: nsm\_sensor\_ps-stop should kill the processes tailing the snort.stats files
    * [Issue 654](https://github.com/dougburks/security-onion/issues/654): NSM: set SNORT\_PERF\_STATS in snort\_agent.conf to 0 when ENGINE=suricata
    * [Issue 643](https://github.com/dougburks/security-onion/issues/643): Rotate logs in /var/log/nsm/
    * [Issue 571](https://github.com/dougburks/security-onion/issues/571): securityonion-web-page: add Security Onion cheat sheet PDF
    * [Issue 644](https://github.com/dougburks/security-onion/issues/644): sostat-quick: check server/sensor
    * [Issue 692](https://github.com/dougburks/security-onion/issues/692): sostat: list number of ELSA buffers in queue and warn if higher than 10
    * [Issue 701](https://github.com/dougburks/security-onion/issues/701): sostat: include number of CPU cores
    * [Issue 591](https://github.com/dougburks/security-onion/issues/591): Bro Intel Whitelist
    * [Issue 418](https://github.com/dougburks/security-onion/issues/418): netsniff-ng 0.58 or higher
    * [Issue 492](https://github.com/dougburks/security-onion/issues/492): CapMe needs to handle UDP better
    * [Issue 493](https://github.com/dougburks/security-onion/issues/493): CapMe: send credentials interactively to avoid exposing on command line
    * [Issue 608](https://github.com/dougburks/security-onion/issues/608): Update bash scripts to use /bin/sh
    * [Issue 547](https://github.com/dougburks/security-onion/issues/547): sosetup: if enabling salt on a sensor, check top.sls to make sure it doesn't already exist
    * [Issue 304](https://github.com/dougburks/security-onion/issues/304): sosetup: support unique interface names
    * [Issue 605](https://github.com/dougburks/security-onion/issues/605): sosetup: replace tmp with mktemp
    * [Issue 596](https://github.com/dougburks/security-onion/issues/596): sosetup: sensor should stop/disable Apache and Snorby worker
    * [Issue 693](https://github.com/dougburks/security-onion/issues/693): sosetup: improve input validation for email address
    * [Issue 592](https://github.com/dougburks/security-onion/issues/592): sosetup: add -y option
    * [Issue 593](https://github.com/dougburks/security-onion/issues/593): sosetup: checking for Internet access takes a while if DNS doesn't immediately fail
    * [Issue 480](https://github.com/dougburks/security-onion/issues/480): sosetup: running on sensor should automatically create autossh account on server
    * [Issue 500](https://github.com/dougburks/security-onion/issues/500): sosetup: restart starman (may not be necessary)
    * [Issue 504](https://github.com/dougburks/security-onion/issues/504): sosetup: avoid running securityonion\_elsa\_register.rb twice
    * [Issue 532](https://github.com/dougburks/security-onion/issues/532): sosetup: Limit what autossh keys can do
    * [Issue 559](https://github.com/dougburks/security-onion/issues/559): sosetup: support for NIC bonding configuration
  * May 2015
    * [Issue 603](https://github.com/dougburks/security-onion/issues/603): securityonion-bro-scripts: drwatson
    * [Issue 604](https://github.com/dougburks/security-onion/issues/604): ELSA: parsers for Bro drwatson logs
    * [Issue 558](https://github.com/dougburks/security-onion/issues/558): Add VirusTotal uploader
    * [Issue 369](https://github.com/dougburks/security-onion/issues/369): Arpwatch
    * [Issue 657](https://github.com/dougburks/security-onion/issues/657): ELSA: email check
    * [Issue 651](https://github.com/dougburks/security-onion/issues/651): ELSA: starman restart doesn't work properly
    * [Issue 464](https://github.com/dougburks/security-onion/issues/464): Consider changing default query\_timeout in /etc/elsa\_web.conf
    * [Issue 331](https://github.com/dougburks/security-onion/issues/331): securityonion-elsa: update dependencies
    * [Issue 336](https://github.com/dougburks/security-onion/issues/336): When configuring ELSA log node, change MySQL port using /etc/mysql/conf.d/
    * [Issue 385](https://github.com/dougburks/security-onion/issues/385): Additional log parsers (non-Bro) for ELSA
    * [Issue 447](https://github.com/dougburks/security-onion/issues/447): ELSA syslog-ng.conf rewrite r\_pipes
    * [Issue 512](https://github.com/dougburks/security-onion/issues/512): ELSA syslog-ng.conf filter f\_bro\_headers
    * [Issue 467](https://github.com/dougburks/security-onion/issues/467): ELSA dashboard for Snort performance
    * [Issue 594](https://github.com/dougburks/security-onion/issues/594): securityonion-sudoers: 10\_securityonion