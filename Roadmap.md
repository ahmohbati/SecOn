Please note that this is all subject to change!
  * January 2015
    * ~~[Issue 655](../issues/655): Suricata 2.0.5~~
    * ~~[Issue 658](../issues/658): NSM: fix umask on Snort unified2 output~~
    * ~~[Issue 548](../issues/548): NSM: run barnyard2 as non-root user~~
    * ~~[Issue 649](../issues/649): nsm\_all\_del\_quick: check for /etc/nsm/servertab and /etc/nsm/sensortab before trying to read~~
    * ~~[Issue 598](../issues/598): so-snorby-wipe~~
    * ~~[Issue 610](../issues/610): NSM: ossec\_agent alert level should be configurable~~
    * ~~[Issue 660](../issues/660): Setup: add OSSEC\_AGENT\_LEVEL to /etc/nsm/securityonion.conf~~
    * ~~[Issue 656](../issues/656): ELSA: update parser for bro\_conn to parse country code~~
    * ~~[Issue 659](../issues/659): securityonion-web-page: add ELSA query for bro\_conn groupby:resp\_country\_code~~
    * ~~[Issue 667](../issues/667): New packages for shellshock and malware-traffic-analysis samples~~
    * ~~[Issue 673](../issues/673): Suricata 2.0.6~~
    * ~~[Issue 642](../issues/642): Update Salt packages/scripts to 2014.7.0~~
    * ~~[Issue 619](../issues/619): Onionsalt: backup /opt/onionsalt/pillar/top.sls~~
    * ~~[Issue 661](../issues/661): Onionsalt: replicate /usr/local/lib/snort\_dynamicrules/~~
    * ~~[Issue 672](../issues/672): sguil-db-purge: check for UNCAT\_MAX~~
    * ~~[Issue 663](../issues/663): sosetup: sosetup.conf SGUIL\_CLIENT\_PASSWORD\_1 should say Sguil/Squert/ELSA/Snorby~~
    * ~~[Issue 664](../issues/664): sosetup: run Bro as non-root user~~
    * ~~[Issue 666](../issues/666): sostat: run Bro as non-root user~~
    * ~~[Issue 665](../issues/665): NSM: run Bro as non-root user~~
    * ~~[Issue 676](../issues/676): NSM: run Sguil as non-root user~~
    * ~~[Issue 671](../issues/671): NSM: /etc/cron.d/sensor-clean needs 2>&1~~
  * February 2015
    * ~~[Issue 668](../issues/668): ELSA: pdbtool errors~~
    * ~~[Issue 669](../issues/669): ELSA: update parsers for Bro DNS and BIND~~
    * ~~[Issue 670](../issues/670): securityonion-web-page: add queries for updated bro\_dns parser~~
    * ~~[Issue 685](../issues/685): securityonion-web-page: update links~~
    * ~~[Issue 684](../issues/684): NSM: nsm\_server\_ps-start needs to create /var/log/sguild/ if it doesn't already exist~~
    * ~~[Issue 686](../issues/686): NSM: nsm\_server\_ps-start needs to set permissions on /var/log/nsm/so-elsa/ properly~~
    * ~~[Issue 687](../issues/687): NSM: nsm\_sensor\_ps-start should set permissions on /var/log/nsm/ properly~~
    * ~~[Issue 689](../issues/689): NSM: add USE\_DNS option to ossec\_agent.conf~~
    * ~~[Issue 688](../issues/688): ossec\_agent: add option to disable DNS lookups~~
    * ~~[Issue 680](../issues/680): Bro 2.3.2~~
    * ~~[Issue 683](../issues/683): securityonion-et-rules: update for new ISO~~
    * ~~[Issue 632](../issues/632): ISO: add bridge-utils~~
    * ~~[Issue 601](../issues/601): ISO: add foremost~~
    * ~~[Issue 614](../issues/614): ISO: add securityonion-samples-shellshock~~
    * ~~[Issue 662](../issues/662): ISO: add securityonion-samples-mta~~
    * ~~[Issue 675](../issues/675): ISO: add xfsprogs~~
    * ~~[Issue 602](../issues/602): 12.04.5.1 ISO image~~
  * March 2015
    * ~~[Issue 695](../issues/695): Suricata 2.0.7~~
    * ~~[Issue 696](../issues/696): ELSA custom menu~~
    * ~~[Issue 691](../issues/691): NSM: chown -R $BRO\_USER:$BRO\_GROUP /nsm/bro >/dev/null 2>&1~~
    * ~~[Issue 698](../issues/698): NSM: nsm\_server\_del line 170 echo\_msg 0 "Deleting server: $SERVER\_NAME"~~
    * ~~[Issue 699](../issues/699): NSM: Bro node.cfg host=localhost~~
    * ~~[Issue 700](../issues/700): Setup: Bro node.cfg host=localhost~~
    * ~~[Issue 702](../issues/702): Snort 2.9.7.2~~
    * ~~[Issue 703](../issues/703): Move from Google Code to Github~~
    * ~~[Issue 706](../issues/706): Add Josh Brower's ELSA parsers for process logs and sysmon~~
    * ~~[Issue 709](../issues/709): Add fear.nothing's ELSA parsers for pfSense~~
    * ~~[Issue 710](../issues/710): securityonion-web-page: add ELSA queries for Firewall logs and Windows Processes~~
  * April 2015
    * ~~[Issue 711](../issues/711): Add "date" command to /usr/bin/sguil-db-purge~~
    * ~~[Issue 692](../issues/692): sostat: list number of ELSA buffers in queue and warn if higher than 20~~
    * ~~[Issue 701](../issues/701): sostat: include number of CPU cores~~
    * ~~[Issue 681](../issues/681): rule-update: wipe snort\_dynamicrules directory on sensor~~
    * ~~[Issue 677](../issues/677): rule-update: create /usr/local/lib/snort\_dynamicrules/ if it doesn't already exist~~
    * ~~[Issue 678](../issues/678): rule-update: /etc/cron.d/rule-update should have 2>&1~~
    * ~~[Issue 697](../issues/697): rule-update: log snorby reference table update to barnyard2-snorby.log~~
    * ~~[Issue 679](../issues/679): rule-update: run pulledpork as unprivileged user~~
    * ~~[Issue 715](../issues/715): securityonion-rule-update: sensor-only boxes running salt shouldn't try to copy /etc/cron.d/rule-update~~
  * May 2015
    * ~~[Issue 725](../issues/725): Suricata 2.0.8~~
    * ~~[Issue 718](../issues/718): Sphinx 2.1.9~~
    * ~~[Issue 241](../issues/241): NSM scripts should have a timeout period when stopping services~~
    * ~~[Issue 392](../issues/392): Patch for lib-nsm-common-utils from Mark Seiden~~
    * ~~[Issue 714](../issues/714): nsm_server_user-disable~~
    * ~~[Issue 705](../issues/705): ossec\_agent: improvements from Brian Kellogg~~
    * ~~[Issue 716](../issues/716): ossec_agent: tighten regex to only look for -> anchored to hostname or IP~~
    * ~~[Issue 717](../issues/717): ossec_agent: send alerts to sguild immediately instead of waiting for next alert~~
  * June 2015
    * ~~[Issue 742](../issues/742): securityonion-suricata package missing debian/install~~
    * ~~[Issue 730](../issues/730): Snort 2.9.7.3~~
    * ~~[Issue 731](../issues/731): Snort DAQ 2.0.5~~
    * ~~[Issue 657](../issues/657): ELSA 1205~~
    * ~~[Issue 447](../issues/447): ELSA syslog-ng.conf rewrite r\_pipes~~
    * ~~[Issue 512](../issues/512): ELSA syslog-ng.conf filter f\_bro\_headers~~
    * ~~[Issue 726](../issues/726): ELSA syslog-ng.conf - add filesystem destinations~~
    * ~~[Issue 674](../issues/674): ELSA - update bro_notice parser to parse src and dst fields~~
    * ~~[Issue 722](../issues/722): securityonion-web-page: update HTTP mime type queries for ELSA 1205~~
    * ~~[Issue 723](../issues/723): CapMe: Update for new ELSA API~~
    * ~~[Issue 500](../issues/500): sosetup: restart starman~~
    * ~~[Issue 504](../issues/504): sosetup: avoid writing ELSA_PORT twice in SSH_CONF~~
    * ~~[Issue 547](../issues/547): sosetup: if enabling salt on a sensor, check top.sls to make sure it doesn't already exist~~
    * ~~[Issue 740](../issues/740): sosetup: sensor should use sudo to restart apache on master~~
    * ~~[Issue 741](../issues/741): sosetup: sometimes local salt-minion doesn't check in with local salt-master quickly enough~~
    * ~~[Issue 732](../issues/732): NSM: only output color codes if running on a tty~~
    * ~~[Issue 746](../issues/746): ELSA 1205 package enabled perl module on non-ELSA systems~~
    * ~~[Issue 747](../issues/747): ELSA 1205 package duplicated syslog-ng.conf entries on non-ELSA systems~~
    * ~~[Issue 748](../issues/748): ELSA 1205 package didn't add the pid column to the query_log table for upgrades~~
    * ~~[Issue 749](../issues/749): Update tcl-tls package and replace DH512 key with DH2048~~
    * ~~[Issue 751](../issues/751): NSM: change watchdog run time to avoid race condition~~
    * ~~[Issue 744](../issues/744): sosetup: Restart Apache to activate new ELSA apikey~~
    * [Issue 745](../issues/745): OSSEC 2.8.2
    * [Issue 733](../issues/733): 12.04.5.2 ISO image
  * July 2015
    * [Issue 743](../issues/743): Bro 2.4
    * [Issue 752](../issues/752): securityonion-bro-scripts: update sensortab.bro for Bro 2.4
    * [Issue 753](../issues/753): securityonion-bro-scripts: update shellshock module for Bro 2.4
    * [Issue 754](../issues/754): securityonion-bro-scripts: update extract.bro for Bro 2.4
    * [Issue 727](../issues/727): Argus 3.0.8.1
    * [Issue 724](../issues/724): /etc/cron.d/rule-update should avoid overwhelming rule sites
    * [Issue 755](../issues/755): securityonion-elsa-extras: add parser for Bro 2.4 mysql.log
    * [Issue 756](../issues/756): securityonion-elsa-extras: add parser for Bro 2.4 kerberos.log
    * [Issue 757](../issues/757): securityonion-elsa-extras: add parser for Bro 2.4 rdp.log
    * [Issue 758](../issues/758): securityonion-elsa-extras: add parser for Bro 2.4 pe.log
    * [Issue 759](../issues/759): securityonion-elsa-extras: add parser for Bro 2.4 sip.log
    * [Issue 728](../issues/728): securityonion-libcapture-tiny-perl should `Provides: libcapture-tiny-perl`
    * [Issue 690](../issues/690): http\_agent: ---disable-inotify
    * [Issue 615](../issues/615): NSM: add "exit $RET" where necessary
    * [Issue 588](../issues/588): NSM: purge old OSSEC logs
    * [Issue 561](../issues/561): nsm\_server\_backup-config should check FORCE\_YES
    * [Issue 523](../issues/523): sensor-clean: add option to skip removal of bro or argus logs
    * [Issue 534](../issues/534): NSM: Patches for adding PCAP snap length for Netsniff-NG
    * [Issue 645](../issues/645): NSM scripts don't check if a sensor is disabled before performing operations when a --sensor-name= is specified
    * [Issue 652](../issues/652): NSM: barnyard sending blank interface to ELSA
    * [Issue 653](../issues/653): NSM: nsm\_sensor\_ps-stop should kill the processes tailing the snort.stats files
    * [Issue 654](../issues/654): NSM: set SNORT\_PERF\_STATS in snort\_agent.conf to 0 when ENGINE=suricata
    * [Issue 643](../issues/643): Rotate logs in /var/log/nsm/
    * [Issue 571](../issues/571): securityonion-web-page: add Security Onion cheat sheet PDF
    * [Issue 644](../issues/644): sostat-quick: check server/sensor
    * [Issue 591](../issues/591): Bro Intel Whitelist
    * [Issue 418](../issues/418): netsniff-ng 0.5.9
    * [Issue 737](../issues/737): Bro transcript debug output gets rendered in the transcript
    * [Issue 736](../issues/736): CapME: Debug information occasionally gets rendered inside the transcript
    * [Issue 492](../issues/492): CapMe needs to handle UDP better
    * [Issue 738](../issues/738): CapME: handle large pcaps more gracefully
    * [Issue 493](../issues/493): CapMe: send credentials interactively to avoid exposing on command line
    * [Issue 608](../issues/608): Update bash scripts to use /bin/sh
    * [Issue 729](../issues/729): sosetup: add option for pivot URL
    * [Issue 304](../issues/304): sosetup: support unique interface names
    * [Issue 605](../issues/605): sosetup: replace tmp with mktemp
    * [Issue 596](../issues/596): sosetup: sensor should stop/disable Apache and Snorby worker
    * [Issue 693](../issues/693): sosetup: improve input validation for email address
    * [Issue 592](../issues/592): sosetup: add -y option
    * [Issue 593](../issues/593): sosetup: checking for Internet access takes a while if DNS doesn't immediately fail
    * [Issue 480](../issues/480): sosetup: running on sensor should automatically create autossh account on server
    * [Issue 532](../issues/532): sosetup: Limit what autossh keys can do
    * [Issue 559](../issues/559): sosetup: support for NIC bonding configuration
    * [Issue 735](../issues/735): sosetup: Advanced Setup should automatically configure PF_RING instances based on number of CPU cores
  * August 2015
    * [Issue 739](../issues/739): Salt 2015.5.0
    * [Issue 708](../issues/708): OSSEC 2.9
    * [Issue 707](../issues/707): Add Josh Brower's OSSEC decoders/rules for sysmon
    * [Issue 603](../issues/603): securityonion-bro-scripts: drwatson
    * [Issue 331](../issues/331): securityonion-elsa: update dependencies
    * [Issue 604](../issues/604): ELSA: parsers for Bro drwatson logs
    * [Issue 558](../issues/558): Add VirusTotal uploader
    * [Issue 369](../issues/369): Arpwatch
    * [Issue 651](../issues/651): ELSA: starman restart doesn't work properly
    * [Issue 464](../issues/464): Consider changing default query\_timeout in /etc/elsa\_web.conf
    * [Issue 336](../issues/336): When configuring ELSA log node, change MySQL port using /etc/mysql/conf.d/
    * [Issue 467](../issues/467): ELSA dashboard for Snort performance
    * [Issue 594](../issues/594): securityonion-sudoers: 10\_securityonion