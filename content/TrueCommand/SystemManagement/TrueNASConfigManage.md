---
title: "TrueNAS Configuration File Management"
weight: 25
---

TrueCommand automatically backs up the TrueNAS configuration any time there is a database change or a TrueCommand Audit Log entry.
Manual backups can be created as needed.

## Viewing Backups

To view the current TrueNAS configuration backups, open the **Dashboard** and click *Config Backups* to display the **Configuration Backup Window**.

![DashboardSystemConfigManagement](/images/TrueCommand/1.3/DashboardSystemConfigManagement.png "Dashboard: Configuration Backups")

The **Configuration Backup Window** shows a list of backups along with the time and date of their creation.
To create a new backup, click *Create Backup*.

To reset a TrueNAS system to a previous configuration, click the <i class="material-icons" aria-hidden="true" title="History">history</i>icon.
Choose the configuration file to use.
You must reset the TrueNAS system to apply the configuration changes.





### Viewing Backups

Open the TrueCommand Dashboard.

DashboardView.png

Click on the system name for a TrueNAS server to open the Single System view.

DashboardSingleSystemView.png

Click the **Config Backups** Button to open the config backup window



### Create a config backup

ConfigBackupsCreate.png


### Apply a config backup


ConfigBackupsList.png



### Delete a config backup


ConfigBackupDelete.png







