---
title: "Users"
weight: 20
---

In TrueNAS, user accounts allow flexibility for accessing shared data.
A common practice is to create users and assign them to [groups]({{< relref "Groups.md" >}}).
This allows for efficient permissions tuning for large numbers of users.

{{< hint info >}}
Only the *root* user account can log in to the TrueNAS web interface.
{{< /hint >}}

When the network uses a directory service, import the existing account information using the instructions in [Directory Services](https://www.truenas.com/docs/core/directoryservices/).
Using [Active Directory]({{< relref "ActiveDirectory.md" >}}) requires setting Windows user passwords inside Windows.

To see user accounts, go to **Accounts > Users**.

![AccountsUsersList](/images/CORE/12.0/AccountsUsersList.png "List of User Accounts")

TrueNAS hides all built-in users by default. To see all built-in users, click <i class="material-icons" aria-hidden="true" title="Settings">settings</i> and **SHOW**.

## Creating User Accounts

To create a new user, go to **Accounts > Users** and click *ADD*.

![Accounts Users Add](/images/CORE/12.0/AccountsUsersAdd.png "Accounts Users Add")

Account options are subdivided into groups of similar options.

{{< tabs "Account Options" >}}
{{< tab "Identification" >}}

### Identification

Enter the *Full Name* of the user.
A simplified *Username* is suggested from the *Full Name*, but can be overridden with your own choice.

An *Email* address can be associated with an user account.

Set and confirm a password for the user.
{{< /tab >}}
{{< tab "User ID and Groups" >}}
### User ID and Groups

Next, a user ID must be set.
TrueNAS automatically suggests the user ID, starting at *1000*.
This suggestion can be changed if desired.
It is recommended to use an ID of *1000* or more for non built-in users.

By default, TrueNAS creates a new primary group with the same name as the user.
To instead add the user to an existing primary group, unset *New Primary Group* and select an existing group from the *Primary Group* drop-down.
The user can be added to additional groups using the *Auxiliary Groups* drop-down.
{{< /tab >}}
{{< tab "Directories and Permissions" >}}
### Directories and Permissions

When creating a user, the home directory path is set to <file>/nonexistent</file>.
This does not create a home directory for the user.
To set a home directory for the user, select a path using the file browser.
If the directory exists and matches the user name, it is set as the user home directory.
When the path does not end with a subdirectory matching the user name, a new subdirectory is created.
The full path to the users home directory is shown here when editing a user.

Directly under the file browser, the home directory permissions can be set.
TrueNAS default user accounts cannot have their permissions changed.
{{< /tab >}}
{{< tab "Authentication" >}}
### Authentication
A public SSH key can be assigned to a user for key based authentication.
Just paste the *public* key into the *SSH Public Key* field.
If you are using an SSH public key, it is always a good idea to keep a backup of the key.
Click *DOWNLOAD SSH PUBLIC KEY* to download the pasted key as a <file>.txt</file> file.

When *Disable Password* is *Yes*, the *Password* field becomes unavailable.
Any existing password is removed from the account.
The *Lock User* and *Permit Sudo* options are also removed.
The account is then restricted from password-based logins for services.
For example, disabling the password prevents using account credentials to log in to an SMB share or open an SSH session on the system.
By default, *Disable Password* is *No*.

A specific [shell]({{< relref "Shell.md" >}}) can be set for the user from the *Shell* drop-down:

| Shell | Description |
|-------|-------------|
| csh	| [C shell](https://docs.freebsd.org/44doc/usd/04.csh/paper.html) for UNIX system interactions. |
| sh	| [Bourne shell](https://www.in-ulm.de/~mascheck/bourne/v7/) |
| tcsh	| [Enhanced C shell](https://www.tcsh.org) that includes editing and name completion. |
| bash	| [Bourne Again shell](https://www.gnu.org/software/bash/manual/bash.html) for the GNU operating system. |
| ksh93	| [Korn shell](http://www.kornshell.com) that incorporates features from both *csh* and *sh*. |
| mksh	| [MirBSD Korn Shell](https://www.mirbsd.org/mksh.htm) |
| rbash	| [Restricted bash](https://www.gnu.org/software/bash/manual/html_node/The-Restricted-Shell.html) |
| rzsh	| [Restricted zsh](https://www.csse.uwa.edu.au/programming/linux/zsh-doc/zsh_14.html) |
| scponly | [scponly](https://github.com/scponly/scponly/wiki) restricts the user's SSH usage to only the `scp` and `sftp` commands. |
| zsh	| [Z shell](http://zsh.sourceforge.net/) |
| git-shell | [restricted git shell](https://git-scm.com/docs/git-shell) |
| nologin | Use when creating a system account or to create a user account that can authenticate with shares but which cannot log in to the TrueNAS system using `ssh`.

Setting *Lock User* disables all password-based functionality for this account until the option is unset.

*Permit Sudo* allows this account to act as the system administrator using the `sudo` command.
For better security, leave this option disabled.

When the user account is going to be using a *Windows 8* or newer client to access data stored on TrueNAS, set *Microsoft Account*.
This enables additional authentication methods available from those operating systems.

By default, *Samba Authentication* is enabled.
This allows using the account credentials to access data shared with [SMB]({{< relref "SMBShare.md" >}}).
{{< /tab >}}
{{< /tabs >}}
