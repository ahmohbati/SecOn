#### Preamble ####

The http\_agent for Sguil was created to add URL events (httpry, Suricata, Bro) to Sguil. This page outlines the usage scenarios for this agent.

It is important to note that in most cases (> 50,000 URLs/day) you do not want this agent to place all URL data into your database, that is not what it was designed for. This agent is intended to complement your signatures; running with a customized exclusions file that is tailored to your environment.

If you have enabled ELSA, then you already have Bro HTTP logs there and should probably disable http\_agent to avoid duplicating effort.

#### Using the http\_agent with Sguil ####

If you have a small installation and want to put all URLs into the database it is wise to autocat these events. This can be achieved by adding the following line to Sguil's autocat.conf:

```
none||ANY||ANY||ANY||ANY||ANY||ANY||%%REGEXP%%^URL||1
```
<p>
If you want to use it to treat unfamiliar or specific URLs as events then you will need to setup the exclusions file. This file can be used in one of two ways:<br>
<br>
1) If INVERT_MATCH is set to 0 in http_agent.conf anything that matches an entry in http_agent.exclude will be ignored.<br>
<br>
2) If INVERT_MATCH is set to 1 in http_agent.conf anything that matches an entry in http_agent.exclude will be sent to Sguild.<br>
<br>
<br>
<b>Example 1: Match everything from the following TLD's (INVERT_MATCH set to 1)</b>

<pre><code>*.ua<br>
*.ru<br>
*.cn<br>
*.lv<br>
</code></pre>


<b>Example 2: Ignore everything from the following FQDN's (INVERT_MATCH set to 0)</b>

<pre><code>*.facebook.com<br>
*.dropbox.com<br>
*.twitter.com<br>
</code></pre>