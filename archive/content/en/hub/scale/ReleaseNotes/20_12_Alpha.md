---
title: "SCALE 20.12-ALPHA (Angelfish)"
tags: ["SCALE"]
---

**December 18, 2020**

iXsystems is pleased to release the next Alpha version of TrueNAS SCALE!
SCALE is the newest member of the TrueNAS family.
When complete, SCALE will have all major TrueNAS CORE storage and sharing features and web interface based on Debian GNU/Linux.
There will also be additional SCALE-specific features that are derived from the application’s Linux base.
The major features of SCALE are represented in the application acronym:

<ul style="list-style: none;">
	<li><b>S</b>caled-Out ZFS</li>
	<li><b>C</b>onverged</li>
	<li><b>A</b>ctive-Active</li>
	<li><b>L</b>inux Containers</li>
	<li><b>E</b>asy to Manage</li>
</ul>

Initial developer’s notes for TrueNAS SCALE are available on the TrueNAS Documentation Hub at https://www.truenas.com/docs/hub/scale/dev-notes/.
Note that because SCALE shares a similar user interface as the FreeBSD-based TrueNAS CORE, many of the current documentation articles also apply to SCALE.
SCALE feature-specific articles will be added to https://www.truenas.com/docs/hub/scale/ as the software approaches its first full release.

Code-named Angelfish, TrueNAS SCALE-ALPHA follows a year.month scheme for versioned releases.
Because this is an ALPHA release of the software, not all planned features are present.
The status of major features are listed here, along with the full changelog of bug fixes that are part of the SCALE 20.12-ALPHA release.

## Software Features

### Verified

Verified Features are generally working in SCALE. Minor bugs could be present.

* Pool Management
* SMB Shares
* iSCSI Shares
* NFS Shares
* S3 Shares
* AFP Shares
* AD / LDAP Directory Services
* Online / Offline updating
* Virtual Machines (Using KVM)
* WebDAV
* Monitoring, Alerting and Reporting
* POSIX 1e support
* Boot Environments
* SSH Credentials
* ZFS Encryption
* Cloud Sync
* Replication
* TrueCommand Cloud connections

### Provisional

These features have been added, but have known issues or are not fully feature-complete.
Please use only with caution.

* [Applications UI](/hub/scale/dev-notes/#using-applications)
* Tasks:
  * Cron
  * Init/Shutdown Scripts
  * S.M.A.R.T. testing
  * Resilver prioritization
  * Periodic Snapshots
  * Rsync
  * Scrub
* [Docker Images deployed as Helm Charts with Kubernetes NVIDIA / Intel Quicksync GPU passthrough (CLI)](/hub/scale/dev-notes/#using-kubernetes)
* Wireguard (CLI)
* Networking and Settings UX Refresh
* OpenVPN Client and Server
* Two-factor authentication
* Certificate Management

### Experimental

These features are still in early development and will be landing in Nightly images of SCALE in the near future. 

* Clustered Datasets API support for TrueCommand
* TrueCommand Clustering UI for SCALE
* NFSv4 ACL support

## Change Log

### New Feature

<ul>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-100018'>NAS-100018</a>] -         S.M.A.R.T tests not sticky when disk is replaced
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-104324'>NAS-104324</a>] -         Platform dependent IPMI plugin
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-104374'>NAS-104374</a>] -         Google requiring oauth for sending mail starting June 2020
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-105082'>NAS-105082</a>] -         Allow hiding network interfaces from dashboard.
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107305'>NAS-107305</a>] -         TrueNAS User Performance Monitoring
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107619'>NAS-107619</a>] -         Tuneables for M-Series Gen3
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107628'>NAS-107628</a>] -         Support IPv6 for HA
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107864'>NAS-107864</a>] -         GMail OAuth when configuring e-mail
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107923'>NAS-107923</a>] -         TrueCommand Icon: un-grey it
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108039'>NAS-108039</a>] -         Kubernetes Catalog Support
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108068'>NAS-108068</a>] -         Add iftop option for SNMP service
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108070'>NAS-108070</a>] -         Add properties_override replication option
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108074'>NAS-108074</a>] -         Bind services to 0.0.0.0 when removing IP address from interface configuration
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108166'>NAS-108166</a>] -         R-Series support in enclosure API
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108271'>NAS-108271</a>] -         New alert service: Telegram
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108322'>NAS-108322</a>] -         Applications UI implementation
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108323'>NAS-108323</a>] -         Add cloud credentials pCloud &quot;hostname&quot; field
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108329'>NAS-108329</a>] -         R-Series Dashboard widget product images
</li>
</ul>

### Improvement

<ul>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-102208'>NAS-102208</a>] -         Disable the ability to create pools, etc on an HA system with mismatched TN versions
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-105947'>NAS-105947</a>] -         Add regression testing for netwait
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107463'>NAS-107463</a>] -         Allow creating encrypted dataset on receiving side
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107495'>NAS-107495</a>] -         Assign new Extent to existing Target
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107498'>NAS-107498</a>] -         iSCSI filter by FC/iSCSI/BOTH
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107507'>NAS-107507</a>] -         Prompt user to add Kerberos keytab entries as needed in NFS form.
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107534'>NAS-107534</a>] -         Create dashboard for Backup Credentials
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107651'>NAS-107651</a>] -         Metadata (Special) Small Block Size
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107661'>NAS-107661</a>] -         Rename Initiators in iSCSI
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107694'>NAS-107694</a>] -         Expose option to enable / disable TRIM in Advanced Menu
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107706'>NAS-107706</a>] -         Make a global titlebar component with optional breadcrumbs
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107735'>NAS-107735</a>] -         Create Dashboard for Certificates
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107751'>NAS-107751</a>] -         Make Save Config easier to find
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107788'>NAS-107788</a>] -         Add extra ZFS ARC stats to reporting.realtime
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107789'>NAS-107789</a>] -         Current bandwidth % per interface on reporting.realtime 
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107790'>NAS-107790</a>] -         Add pool.query event
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107791'>NAS-107791</a>] -         Add pool.dataset.query event
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107793'>NAS-107793</a>] -         Add *.query event
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107819'>NAS-107819</a>] -         12 interfaces to SCALE
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107823'>NAS-107823</a>] -         Proxy collectd graphite stream
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107829'>NAS-107829</a>] -         Overall system disks stats in reporting.realtime
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107830'>NAS-107830</a>] -         Add call to return non-idle processes
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107902'>NAS-107902</a>] -         Turbostat In TrueNAS Scale
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107905'>NAS-107905</a>] -         When usage collection is disabled - Only report the total capacity
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107929'>NAS-107929</a>] -         zfs/snpashot endpoint only returns &quot;false&quot; on failure
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107944'>NAS-107944</a>] -         Use new TrueCommand logo
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107994'>NAS-107994</a>] -         Gluster Config does not persist Upgrades
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108108'>NAS-108108</a>] -         Python with debug and no optimizations
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108156'>NAS-108156</a>] -         Redundant forms on Network Page
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108173'>NAS-108173</a>] -         Increase vCore limit for KVM under SCALE
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108189'>NAS-108189</a>] -         Add HA platform detection for bhyve
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108213'>NAS-108213</a>] -         Iconic template icon does not work on white background
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108348'>NAS-108348</a>] -         Slide out dataset options form
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108349'>NAS-108349</a>] -         Slide out zvol create/edit form
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108359'>NAS-108359</a>] -         No ix-auto in Test Changes, Revert Changes changes button
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108360'>NAS-108360</a>] -         Fix ix-auto directives on Storage page Global Actions
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108391'>NAS-108391</a>] -         Slide out pool import wizard
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108495'>NAS-108495</a>] -         Missing ix-auto in -&gt; and + button in Sharing/iSCSI/Initiators/Add on 12.0
</li>
</ul>

### Bugs

<ul>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-102006'>NAS-102006</a>] -         Improve Alert Settings page
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-104668'>NAS-104668</a>] -         Make SED disks handling platform dependent
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-105156'>NAS-105156</a>] -         Upgraded to 11.3, Cloud Sync to B2 rclone failing
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-106351'>NAS-106351</a>] -         remove code related to hardware older than z-series
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-106424'>NAS-106424</a>] -         Add support for Xen/XCP-ng xe-guest-utilities
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107187'>NAS-107187</a>] -         Disks page does not show Pool affiliation in Pool column
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107317'>NAS-107317</a>] -         Replication progress % Incorrect
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107318'>NAS-107318</a>] -         replication target as non-root cannot mount
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107354'>NAS-107354</a>] -         Package remote-pdb in SCALE
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107384'>NAS-107384</a>] -         2FA for SSH plus LDAP ignores 2FA
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107419'>NAS-107419</a>] -         Replicated datasets of encrypted pools to another encrypted pool is inaccessible
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107527'>NAS-107527</a>] -         allow creation of failover lagg from netcli
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107577'>NAS-107577</a>] -         Tunables regex prevents editing/creation of valid tunables
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107590'>NAS-107590</a>] -         mDNS not starting? Server not visible to macOS clients
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107600'>NAS-107600</a>] -         iSCSI target deletion via 12rc1 GUI does not remove connection
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107609'>NAS-107609</a>] -         Alerts for  NFS services could not bind to specific IP addresses, using 0.0.0.0.
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107638'>NAS-107638</a>] -         Deleting mountpoint of a jail doesn&#39;t update UI
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107643'>NAS-107643</a>] -         glusterd service api
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107644'>NAS-107644</a>] -         glusterd-events service api
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107646'>NAS-107646</a>] -         GUI shouldn&#39;t allow IPv6 to be attempted on HA
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107647'>NAS-107647</a>] -         ZFS dataset creation can fail with UTF decode error
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107677'>NAS-107677</a>] -         ensure glusterd related services are started after zpool import service
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107678'>NAS-107678</a>] -         hide vhid option on SCALE HA webUI
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107697'>NAS-107697</a>] -         WebUI makes firefox 80.0.1 hang
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107702'>NAS-107702</a>] -         Misleading validation in EDIT IDMAP dialogue
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107713'>NAS-107713</a>] -         Saving ACLs aborted on click
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107737'>NAS-107737</a>] -         IP address cannot be modified
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107753'>NAS-107753</a>] -         Ldap Messages for root and operator
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107784'>NAS-107784</a>] -         nfs alias issues on SCALE
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107800'>NAS-107800</a>] -         SCALE HA webUI side-bar issues
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107808'>NAS-107808</a>] -         &quot;File ticket&quot; form fields are not aligned
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107809'>NAS-107809</a>] -         Attaching screenshots to &quot;File ticket&quot; form has no visual feedback
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107832'>NAS-107832</a>] -         Network activity does not seem to be behaving properly on dashboard
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107840'>NAS-107840</a>] -         Broken ACL editor shown after creating home share
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107845'>NAS-107845</a>] -         fix device.get_disks on SCALE HA
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107851'>NAS-107851</a>] -         Make dns_domain_name optional in idmap form
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107857'>NAS-107857</a>] -         replace lshw in ixdiagnose with alternative
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107860'>NAS-107860</a>] -         replace lshw in device.get_info GPU with alternative
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107873'>NAS-107873</a>] -         SCALE: Adding Static Route does not show up on Summary page
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107884'>NAS-107884</a>] -         &quot;Network connectivity will be interrupted.&quot; message is incorrect
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107888'>NAS-107888</a>] -         change &quot;FreeNAS&quot; to &quot;TrueNAS&quot; in vmware plugin
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107892'>NAS-107892</a>] -         Cloud sync task &quot;Advance options&quot; should probably be &quot;Advanced options&quot;
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107907'>NAS-107907</a>] -         add better validation to update.manual API
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107914'>NAS-107914</a>] -         TrueNAS alerted me to a NextCloud update, but the updater says it was already up to date
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107918'>NAS-107918</a>] -         sas2flash segmentation fault
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107927'>NAS-107927</a>] -         NFS cannot bind IP
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107928'>NAS-107928</a>] -         CLONE - CPU temperature graph always has a drop to zero at the end
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107933'>NAS-107933</a>] -         Periodic snapshot task calendar is broken
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107948'>NAS-107948</a>] -         [User error] Ability to delete System Dataset is too easy - UI suggestions.
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107955'>NAS-107955</a>] -         Internal services classes showing up in API docs
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107957'>NAS-107957</a>] -         middlewared crashing too many files no login
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107987'>NAS-107987</a>] -         [SCALE] Fails to change nginx HTTP listen port for WebUI
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107988'>NAS-107988</a>] -         Can&#39;t delete newly created user on SCALE
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-107992'>NAS-107992</a>] -         proftpd starts in SCALE after pool import
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108005'>NAS-108005</a>] -         Replication Task: divide by zero
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108010'>NAS-108010</a>] -         ntb0 broken on upgrade to 12.0-RELEASE
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108020'>NAS-108020</a>] -         iSCSI CHAP passwords incorrect after upgrade to 12.0-RELEASE
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108023'>NAS-108023</a>] -         email save throws an error
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108024'>NAS-108024</a>] -         Add GUI deprecation warning for samba_schema in LDAP plugin
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108031'>NAS-108031</a>] -         Retry download of update
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108047'>NAS-108047</a>] -         make sure HA SCALE accounts for IPv6
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108048'>NAS-108048</a>] -         investigate link-local IPv6 address removal on SCALE
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108050'>NAS-108050</a>] -         SNMP consuming 100% CPU and becomes unavailable
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108056'>NAS-108056</a>] -         Ignore/reset zfs mountpoint property on ZFS replication task
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108059'>NAS-108059</a>] -         Only submit usage stats from the MASTER node if failover licensed
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108064'>NAS-108064</a>] -         only ask for subnet mask once on HA systems
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108065'>NAS-108065</a>] -         change verbiage in network section for HA systems
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108067'>NAS-108067</a>] -         Kerberos Ticket not refreshed (regression)
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108071'>NAS-108071</a>] -         typo in EUI64 ipv6 link-local generation and only generate if one doesn&#39;t exist
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108072'>NAS-108072</a>] -         keepalived.conf indentation issue
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108075'>NAS-108075</a>] -         FreeNAS fails to create alert for failed power supply that IPMI does detect as failed
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108085'>NAS-108085</a>] -         Pool disk details duplicated on other pool&#39;s frame in dashboard
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108087'>NAS-108087</a>] -         Bad GPTID label text
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108089'>NAS-108089</a>] -         CPU widget temperature legend color doesn&#39;t match bar color 
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108097'>NAS-108097</a>] -         Time Machine not advertised after unlocking dataset until SMB is manually restarted
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108102'>NAS-108102</a>] -         Fix routing from pool manager to storage page
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108110'>NAS-108110</a>] -         Exporting pool(s) on TrueNAS 12.0-RELEASE
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108117'>NAS-108117</a>] -         Replication task fails when created with a throttle
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108120'>NAS-108120</a>] -         API v2 regression broke user creation
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108124'>NAS-108124</a>] -         Periodic Snapshot Task Creation allows use of inappropriate characters (i.e. forward slash &quot;/&quot;) in snapshot name
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108129'>NAS-108129</a>] -         Truenas SCALE UI broken for VM creation
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108140'>NAS-108140</a>] -         make sure ix-postinit runs as one of the last services in startup
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108141'>NAS-108141</a>] -         [SCALE] Shares cannot support both NFS and SMB
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108144'>NAS-108144</a>] -         UPS connection lost after failover
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108155'>NAS-108155</a>] -         Missing global action buttons for network dashboard
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108171'>NAS-108171</a>] -         stripe option is deprecated in gluster
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108183'>NAS-108183</a>] -         UPS shutdown leaves passive up on HA system
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108185'>NAS-108185</a>] -         Pull replication fails - ps command has wrong (missing) flags
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108204'>NAS-108204</a>] -         [SCALE] nfsv4 shares do not export properly
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108209'>NAS-108209</a>] -         Add delete call to VMWare Snapshot in SCALE
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108210'>NAS-108210</a>] -         Remove unneeded first step for Import Pool wizard for SCALE
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108220'>NAS-108220</a>] -         Replication failed: cannot send &lt;snapshot name&gt;: encrypted dataset may not be sent with properties without the raw flag
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108222'>NAS-108222</a>] -         pull replication seems ummount replicated dataset
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108223'>NAS-108223</a>] -         hide &quot;.glusterfs&quot; from pool.dataset.query
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108235'>NAS-108235</a>] -         sysctl rc script is running twice on boot breaking carp.allow
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108240'>NAS-108240</a>] -         I cannot change the LAGG protocol type in the aggregation setting in WebUI
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108273'>NAS-108273</a>] -         Traceback printed on VM operations
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108278'>NAS-108278</a>] -         add ability to set quota on gluster volumes
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108279'>NAS-108279</a>] -         Truenas Scale : UPS monitor password is mandatory but it is not shown and error message is unclear
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108282'>NAS-108282</a>] -         return verbose information from gluster.volume.status by default
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108286'>NAS-108286</a>] -         Can&#39;t connect to pCloud
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108288'>NAS-108288</a>] -         duplicate shell entries local users
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108292'>NAS-108292</a>] -         SCALE Shows &quot;Unknown CPU&quot;
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108294'>NAS-108294</a>] -         HA network validation isn&#39;t working
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108302'>NAS-108302</a>] -         Actions button disappeared from the pool status page
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108308'>NAS-108308</a>] -         Cant add google cloud service account
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108313'>NAS-108313</a>] -         failover.control and failover.update are broken on HA systems
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108330'>NAS-108330</a>] -         Snapshot expirations fail when there are too many of them at once
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108331'>NAS-108331</a>] -         plumb the gluster related config into smb plugin API
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108335'>NAS-108335</a>] -         Remove Mirror is not working
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108343'>NAS-108343</a>] -         Error when deleting target in use
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108345'>NAS-108345</a>] -         Cron jobs are blocking each other from running
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108351'>NAS-108351</a>] -         Error (traceback) when editing unrelated properties on dataset with certain zstd (zstandard) compression levels
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108353'>NAS-108353</a>] -         Math error in pool creation dialog
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108354'>NAS-108354</a>] -         unable to delete VM due to XML error
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108371'>NAS-108371</a>] -         UI says replication failed..but it worked
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108376'>NAS-108376</a>] -         Fix console error for tables
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108396'>NAS-108396</a>] -         Linked release notes are to wrong version (11.3U5 -&gt; 12)
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108405'>NAS-108405</a>] -         netatalk is broken on SCALE
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108413'>NAS-108413</a>] -         Make truenas.set_production a job
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108416'>NAS-108416</a>] -         Convert Pool Status Disk Edit to slide out form
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108417'>NAS-108417</a>] -         Make Settings &gt; Change Password into a Dialog
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108423'>NAS-108423</a>] -         Dashboard for CPU &amp; memory do not show values, also reporting is missing
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108473'>NAS-108473</a>] -         &#39;&gt;&#39; not supported between instances of &#39;str&#39; and &#39;Version&#39;
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108475'>NAS-108475</a>] -         CLONE - Error (traceback) when editing unrelated properties on dataset with certain zstd (zstandard) compression levels
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108485'>NAS-108485</a>] -         Repliaction tasks, key-format validation on edit, incorrectly setting all-caps?
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108499'>NAS-108499</a>] -         Remove red border around cron picker
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108504'>NAS-108504</a>] -         Popup on dashboard will not go away
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108520'>NAS-108520</a>] -         high concurrency api requests result in invalid responses
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108529'>NAS-108529</a>] -         [SCALE] Unable to create a debug
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108539'>NAS-108539</a>] -         Reporting graphs missing / rrdcached errors spamming log
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108553'>NAS-108553</a>] -         Degraded pool alert not received in UI or Email
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108560'>NAS-108560</a>] -         Pool status will not update unless system is restarted/system panics
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108562'>NAS-108562</a>] -         Unable to access FTP using &quot;Allow Root Login&quot; option
</li>
<li>[<a href='https://jira.ixsystems.com/browse/NAS-108578'>NAS-108578</a>] -         zettarepl failing to pull-replicate a dataset with canmount=noauto (12.0-U1 regression)
</li>
</ul>
