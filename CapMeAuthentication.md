# CapME Authentication #
Our Setup script automatically configures both Snorby and ELSA to be able to pivot to CapME for full transcripts.  The CapME page will prompt you for username/password and you will enter your normal Sguil/Squert/ELSA username/password.  You have the option of automatically authenticating, but be aware that this will send your username/password in the GET request, so it will be displayed in the browser bar in plaintext.

## Configuring Snorby to auto-authenticate to CapME ##
  * Click "Administration and General Settings".
  * Under OpenFPC, select "Packet capture auto-authenticate" and enter your **Sguil** username and password.
  * Click "Save Settings".

## Configuring ELSA to auto-authenticate to CapME ##
  * Navigate to ELSA -> Preferences:<br>
<br>
<img src='images/elsa/elsa_prefs.png' /><br>
  * Select Actions -> Add New Preference:<br>
<br>
<img src='images/elsa/elsa_prefs_add.png' /><br>
  * Enter the following into the new Preference:<br>
<pre><code>Type = custom<br>
Name = openfpc_username<br>
Value = "your **Sguil** username"<br>
</code></pre>
  * Enter the following into the new Preference:<br>
<pre><code>Type = custom<br>
Name = openfpc_password<br>
Value = "your **Sguil** password"<br>
</code></pre>
  * Close the Preferences window and reload the ELSA page (F5).