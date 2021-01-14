---
title: "System Configuration"
description: "How to change the various system level options in TrueNAS."
weight: 30
---

TrueNAS has numerous settings contained inside the **System > General** and **System > Advanced** screens.
These allow a wide range of system customization, from changing the web interface address, localization options, and data collection to SED, console, and storage options.

## General

**System > General** contains options for configuring the web interface and other basic system settings.

<img src="/images/12.0-system-general.png">
<br><br>

| Setting                       | Value          | Description                                                                                                                                                                                                                                                                                                                                                        |
|-------------------------------|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GUI SSL Certificate           | drop-down menu | The system uses a self-signed certificate to enable encrypted web interface connections. To change the default certificate, select a different created or imported certificate.                                                                                                                                                                                    |
| Web Interface IPv4 Address    | drop-down menu | Choose recent IP addresses to limit the usage when accessing the web interface. The built-in HTTP server binds to the wildcard address of 0.0.0.0 (any address) and issues an alert if the specified address becomes unavailable.                                                                                                                                  |
| Web Interface IPv6 Address    | drop-down menu | Choose recent IPv6 addresses to limit the usage when accessing the web interface. The built-in HTTP server binds to the wildcard address of 0.0.0.0 (any address) and issues an alert if the specified address becomes unavailable.                                                                                                                                |
| Web Interface HTTP Port       | integer        | Allow configuring a non-standard port for accessing the web interface over HTTP. Changing this setting might require changing a [Firefox configuration setting](https://www.redbrick.dcu.ie/~d_fens/articles/Firefox:_This_Address_is_Restricted).                                                                                                                                                                                                     |
| Web Interface HTTPS Port      | integer        | Allow configuring a non-standard port to access the web interface over HTTPS.                                                                                                                                                                                                                                                                                      |
| HTTPS Protocols | drop-down menu | Choose which HTTPS protocols to allow. |
| Web Interface HTTP -> HTTPS Redirect | checkbox       | Redirect HTTP connections to HTTPS. A `GUI SSL Certificate` is required for HTTPS. Activating this also sets the [HTTP Strict Transport Security (HSTS)](https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security) maximum age to 31536000 seconds (one year). This means that after a browser connects to the TrueNAS® web interface for the first time, the browser continues to use HTTPS and renews this setting every year. |
| Language                      | combo box      | Select a language from the drop-down menu. The list can be sorted by `Name` or [Language code](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes). View the translated status of a language in the [webui GitHub repository](https://github.com/freenas/webui/tree/master/src/assets/i18n).                                                                                                                                                                                               |
| Date Format                   | drop-down menu | Select how the Day, Month, and Year are displayed. |
| Console Keyboard Map          | drop-down menu | Select a keyboard layout.                                                                                                                                                                                                                                                                                                                                          |
| Timezone                      | drop-down menu | Select a timezone.                                                                                                                                                                                                                                                                                                                                                 |
| Time Format                   | drop-down menu | Choose how Hours, Minutes, and Seconds are displayed. |
| Crash reporting               | checkbox       | Send failed HTTP request data which can include client and server IP addresses, failed method call tracebacks, and middleware log file contents to iXsystems.                                                                                                                                                                                                      |
| Usage Collection              | checkbox       | Enable sending anonymous usage statistics to iXsystems.                                                                                                                                                                                                                                                                                                            |

After making any changes, click **SAVE**.
Changes to any of the web interface fields can interrupt web interface connectivity while the new settings are applied.

This screen also contains these buttons:

**SAVE CONFIG**: save a backup copy of the current configuration database in the format hostname-version-architecture to the computer accessing the web interface. Saving the configuration after making any configuration changes is highly recommended. TrueNAS® automatically backs up the configuration database to the system dataset every morning at 3:45. However, this backup does not occur if the system is shut down at that time. If the system dataset is stored on the boot pool and the boot pool becomes unavailable, the backup will also not be available. The location of the system dataset can be viewed or set using System ➞ System Dataset.

{{% pageinfo %}}
SSH keys are not stored in the configuration database and must be backed up separately. System host keys are files with names beginning with `ssh_host_` in `/usr/local/etc/ssh/`. The root user keys are stored in `/root/.ssh`.
{{% /pageinfo %}}

There are two types of passwords. User account passwords for the base operating system are stored as hashed values, do not need to be encrypted to be secure, and are saved in the system configuration backup. Other passwords, like iSCSI CHAP passwords, Active Directory bind credentials, and cloud credentials are stored in an encrypted form to prevent them from being visible as plain text in the saved system configuration. The key or seed for this encryption is normally stored only on the operating system device. When **Save Config** is chosen, a dialog gives two options. *Export Password Secret Seed* includes passwords in the configuration file which allows the configuration file to be restored to a different operating system device where the decryption seed is not already present. Configuration backups containing the seed must be physically secured to prevent decryption of passwords and unauthorized access.

{{% alert title="Warning" color="warning" %}}
The **Export Password Secret Seed** option is off by default and should only be used when making a configuration backup that will be stored securely. After moving a configuration to new hardware, media containing a configuration backup with a decryption seed should be securely erased before reuse.
{{% /alert %}}

**Export Pool Encryption Keys** includes the encryption keys of encrypted pools in the configuration file. The encryption keys are restored if the configuration file is uploaded to a system with **UPLOAD CONFIG**.

**UPLOAD CONFIG**: allows browsing to the location of a previously saved configuration file to restore that configuration.

**RESET CONFIG**: reset the configuration database to the default base version. This does not delete user SSH keys or any other data stored in a user home directory. Since configuration changes stored in the configuration database are erased, this option is useful when a mistake has been made or to return a test system to the original configuration.


## Advanced

**System > Advanced** contains more advanced options for configuring system settings.

<img src="/images/SystemAdvanced.png">
<br><br>

| Setting                                   | Value     | Description                                                          |
|-------------------------------------------|-----------|----------------------------------------------------------------------|
| Show Text Console without Password Prompt | checkbox  | Set for the text console to be available without entering a password. |
| Enable Serial Console                     | checkbox  | **Do not** enable this option if the serial port is disabled. Adds the **Serial Port** and **Serial Speed** fields. On UEFI-installed systems, enabling the Serial Console also disables the system video output, including when connecting over the IPMI video console. |
| Serial Port                               | drop down | Select the serial port address in hex. |
| Serial Speed                              | drop down | Select the speed in bps used by the serial port. |
| MOTD Banner                               | string    | Set a message of the day (MOTD) that is shown when a user logs in to the system using SSH. |
| Show Console Messages                     | checkbox  | Display console messages from `/var/log/console.log` in real time at bottom of browser window. Click the console to bring up a scrollable screen. Set the `Stop refresh` option in the scrollable screen to pause updates. Unset to continue watching messages as they occur. When this option is set, a button to show the console log appears on busy spinner dialogs. |
| Show Advanced Fields by Default           | checkbox  | Show all interface configuration advanced fields by default. |
| ATA Security User                         | drop down | User passed to `camcontrol security -u` for unlocking SEDs. Values are *User* or *Master*. |
| SED Password                              | string    | Global password used to unlock Self-Encrypting Drives. |
| Reset SED Password                        | checkbox  | Select to clear the *Password for SED* column of **Storage > Disks**. |
| Swap Size in GiB                          | string    | By default, all data disks are created with the amount of swap specified. Changing the value does not affect the amount of swap on existing disks, only disks added after the change. Does not affect log or cache devices as they are created without swap. Setting to *0* disables swap creation completely. This is STRONGLY DISCOURAGED. |
| LOG (Write Cache) Overprovision Size in GiB | string  | Overprovisioning a ZFS Log SSD can increase its performance and lifespan by distributing writes and erases across more drive flash blocks. Defining a number of GiB here overprovisions ZFS Log disks during pool creation or extension. Examples: 50 GiB, 10g, 5GB. |
| Enable Autotune                           | checkbox  | Enable the Autotune script which attempts to optimize the system based on the installed hardware. Warning: Autotuning is only used as a temporary measure and is not a permanent fix for system hardware issues. |
| Enable Debug Kernel                       | checkbox  | Use a debug version of the kernel on the next boot. |
| Use FQDN for logging                      | checkbox  | Include the Fully-Qualified Domain Name (FQDN) in logs to precisely identify systems with similar hostnames. |
| Syslog Level                              | drop down | When **Syslog Server** is defined, only logs matching this level are sent. |
| Syslog Server                             | string    | Remote syslog server DNS hostname or IP address. Nonstandard port numbers can be used by adding a colon and the port number to the hostname, like `mysyslogserver:1928`. Log entries are written to local logs and sent to the remote syslog server. |
| Syslog Transport                          | drop down | [Transport Protocol](https://tools.ietf.org/html/rfc8095) for the remote system log server connection. Choosing Transport Layer Security (*TLS*) also requires selecting a preconfigured system Certificate. |
| Syslog TLS Certificate                    | drop down | The preconfigured system Certificate to use for authenticating the TLS protocol connection to the remote system log server. |

There is also an option to:

**SAVE DEBUG**: generate text files that contain diagnostic information. After the debug data is collected, the system prompts for a location to save the compressed `.tar` file.

### Autotuning

TrueNAS provides an autotune script which optimizes the system depending on the installed hardware.
For example, if a pool exists on a system with limited RAM, the autotune script automatically adjusts some ZFS sysctl values in an attempt to minimize memory starvation issues.
It should only be used as a temporary measure on a system that hangs until the underlying hardware issue is addressed by adding more RAM.
Autotune will always slow such a system, as it caps the ARC.

> Note: Using the autotuning script is not recommended for TrueNAS Enterprise customers as this can override any specific tunings made by iXsystems Support.

Enabling autotuning will run the autotuner script at boot.
To run the script immediately, reboot the system.

If the autotune script adjusts any settings, the changed values appear in **System > Tunables**.
Note that deleting tunables that were created by autotune only affects the current session, as autotune-set tunables are recreated at boot.
This means that any autotune-set value that is manually changed will revert back to the value set by autotune on reboot.
To permanently change a value set by autotune, change the description of the tunable.
For example, changing the description to manual override prevents autotune from reverting that tunable back to the autotune default value.

When attempting to increase the performance of the TrueNAS system, and particularly when the current hardware may be limiting performance, try enabling autotune.
For those who wish to see which checks are performed, the autotune script is located in `/usr/local/bin/autotune`.
