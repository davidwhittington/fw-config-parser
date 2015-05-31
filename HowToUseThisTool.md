# Introduction #

The creation of this tool was borne out of frustration that there was no useful rule documenting tool for Secure Computing / McAfee Sidewinder products. I wrote this tool as a quick solution and made it available under the GNU General Public License for anyone to use, or re-use for their own environments.

# Details #

To use the tool with Sidewinder perform the following (please note, if this doesn't work, please remove the backslash+newlines from the code block below):

```
srole
foreach fe (accelerator acl adminuser agent antivirus appfilter audit auth burb \
            burbgroup catgroups cert cluster cmd commandcenter config crontab \
            daemond dhcrelay dns domain entrelayd export failover fips fwregisterd \
            geolocation host hostname ids ikmpd interface ipaddr iprange ips ipsec \
            ipsresponse ipssig knownhosts lca license mvm netgroup netmap nss ntp \
            package policy pool proxy qos reports sendmail server service servicegroup \
            snmp ssl static subnet sysctl timeperiod timezone trustedsource \
            udb urltranslation usergroup utt)
echo $fe
cf $fe q >> $fe.config
end
tar cf config.tar *.config
rm *.config
```

Once you've created your TAR file, transfer these files to your processing machine (using sftp, ftp or uuencode/uudecode). Place these files in an appropriate part of your filesystem (either in the main part of your web tree, or just in a directory you can access with your PHP binary).

For the purposes of this document, I've done an export of the Subversion tree into C:\Rules. If you look at the file in C:\Rules\trunk\parser\index.php, you'll see this line:

```
// In relation to this file, where are the configuration files?
$files='../example_configs/sidewinder/';
```

This lets you point to a new directory of configuration files.

I personally run the PHP parser against the rules and output the result straight into an HTML file with this command:

php C:\Rules\trunk\parser\index.php > C:\Rules\sidewinder\_config.html

As at this document's creation date, there is not an example of the output of this result, but you can run this yourself to experiment.