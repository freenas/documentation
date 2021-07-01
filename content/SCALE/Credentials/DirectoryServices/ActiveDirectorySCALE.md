---
title: "Active Directory"
weight: 10
---

{{< toc >}}

The Active Directory (AD) service shares resources in a Windows network.
Because AD provides authentication and authorization services for the users in a network, you do not need to recreate the same user accounts in TrueNAS.

Users can configure AD services on a Windows server running Windows Server 2000 or higher, or on a Unix-like operating system that is running [Samba version 4](https://wiki.samba.org/index.php/Setting_up_Samba_as_an_Active_Directory_Domain_Controller#Provisioning_a_Samba_Active_Directory).
To configure a basic connection, you will need to know the Active Directory domain controller's domain and that system's account credentials.

## Preparation

Before configuring Active Directory, you should take a few steps to ensure the connection process goes smoothly.

{{< tabs "Preparation Steps" >}}
{{< tab "Verify Name Resolution" >}}
To confirm that name resolution is functioning, go to the **Shell** and use `ping` to check the connection to the AD domain controller.

![ShellDomainPingSCALE](/images/SCALE/ShellDomainPingSCALE.png "Pinging a Domain Controller")

When packets are being sent and received without loss, the connection is verified.
Press <kbd>Ctrl + C</kbd> to cancel the `ping`.

Another option is to use `host -t srv _ldap._tcp.domainname.com` to check the SRV records of the network and verify DNS resolution.

{{< expand "The ping failed!" "v" >}}
If the ping fails, go to **Network** and click *Settings* in the *Global Configuration* window. Update the *DNS Servers* and *Default Gateway* settings so the connection to your Active Directory Domain Controller can start.
Use more than one *Nameserver* for the AD domain controllers so that DNS queries for requisite SRV records can succeed.
This helps maintain the AD connection whenever a domain controller becomes unavailable.
{{< /expand >}}
{{< /tab >}}
{{< tab "Time Synchronization" >}}
Active Directory relies on the time-sensitive [Kerberos](https://tools.ietf.org/html/rfc1510) protocol.
During the domain join process, the AD domain controller with the [PDC Emulator FSMO Role](https://support.microsoft.com/en-us/help/197132/active-directory-fsmo-roles-in-windows) is added as the preferred NTP server. 
If your environment requires something different, navigate to **System Settings** and add or edit a server in the *NTP Servers* window.

The time on the system and the AD domain controller cannot be out of sync by more than **five minutes** in a default AD environment.
Use an external time source when configuring a virtualized domain controller.
If the time gets out of sync between TrueNAS and the AD domain controller, the system generates an **Alert**.

There are a few options in TrueNAS to ensure both systems are set to the same time:

* Go to **System Settings > General** and click *Settings* in the *Localization* window to make sure the system *Timezone* matches the AD Domain Controller.

![LocalizationSCALE](/images/SCALE/LocalizationSCALE.png "Timezone Options")

* Set either localtime or universal time in the system BIOS.
{{< /tab >}}
{{< /tabs >}}

## Connect to the Active Directory Domain

To connect to Active Directory, click *Settings* in the *Active Directory* window and enter the AD *Domain Name* and account credentials.
Set *Enable* to attempt to join the AD domain immediately after saving the configuration.

![ActiveDirectorySCALE](/images/SCALE/ActiveDirectorySCALE.png "Active Directory Form")

Advanced options are available for fine-tuning the AD configuration, but the preconfigured defaults are generally suitable.

{{< expand "I can't see any AD information!" "v" >}}
After configuring the Active Directory service, it can take a few minutes for TrueNAS to populate the AD information.
To check the AD join progress, open the <i class="material-icons" aria-hidden="true" title="Assignment">assignment</i> **Task Manager** in the upper-right corner.
Any errors during the join process are also displayed in the **Task Manager**.
{{< /expand >}}

When the import is complete and the TrueNAS cache is enabled (enabled by default), AD users and groups be available when configuring basic dataset permissions or an Access Control List (ACL).

Joining AD also adds default Kerberos realms and generates a default `AD_MACHINE_ACCOUNT` keytab.
TrueNAS automatically begins using this default keytab and removes any administrator credentials that were stored in the TrueNAS configuration file.

## Troubleshooting

If the cache becomes out of sync or fewer users than expected are available in the permissions editors, resync the cache by clicking *Settings* in the *Active Directory* window and selecting *Rebuild Directory Service Cache*.

If the Windows server version is lower than 2008 R2, try creating a **Computer** entry on the Windows server Organizational Unit (OU).
When creating the entry, enter the TrueNAS hostname in the name field.
Make sure it is the same name as the one set in the *Hostname* field in the **Network** section (go to **Network** and find the *Hostname* in the *Global Configuration* window), and the same *NetBIOS alias* from the **Directory Services** section (go to **Directory Services** and click *Settings* in the *Active Directory* window, then click *Advanced Options* and find the *NetBIOS alias*).

{{< expand "Shell Commands" "v" >}}
You can go to **System Settings > Shell** and enter various commands to get more details about the AD connection and users:

* AD current state: `midclt call activedirectory.get_state`.
* Details about the currently connected Lightweight Directory Access Protocol (LDAP) server: `midclt call activedirectory.domain_info | jq`.
  Example:
  ```
  truenas# midclt call activedirectory.domain_info | jq
  {
    "LDAP server": "192.168.1.125",
    "LDAP server name": "DC01.HOMEDOM.FUN",
    "Realm": "HOMEDOM.FUN",
    "Bind Path": "dc=HOMEDOM,dc=FUN",
    "LDAP port": 389,
    "Server time": 1593026080,
    "KDC server": "192.168.1.125",
    "Server time offset": 5,
    "Last machine account password change": 1592423446
  }
  ```
* View AD users: `wbinfo -u`.
  To see more details about a user, enter `getent passwd DOMAIN\\<user>`, replacing `<user>` with the desired user name.
  If `wbinfo -u` shows more users than appear to be available when configuring permissions and the TrueNAS cache is enabled, go to **Directory Services > Active Directory** and increase the *AD Timeout* value.
* View AD groups: `wbinfo -g`.
  To see more details, enter `getent group DOMAIN\\domain\ users`.
* View domains: `wbinfo -m`.
* Test AD connection: `wbinfo -t`. A successful test shows a message similar to `checking the trust secret for domain YOURDOMAIN via RPC calls succeeded`.
* User connection test to an SMB share: `smbclient '//127.0.0.1/smbshare -U AD01.LAB.IXSYSTEMS.COM\ixuser`, replacing `127.0.0.1` with your server address, `smbshare` with the SMB share name, `AD01.LAB.IXSYSTEMS.COM` with your trusted domain, and `ixuser` with the user account name for authentication testing.
{{< /expand >}}
