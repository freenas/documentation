---
title: "Replacing Disks"
description: "How to replace a failed disk."
---

Hard drives or solid-state drives (SSDs) have a finite lifetime and can fail unexpectedly.
When a disk fails in a Stripe (RAID0) pool, the entire pool has to be recreated and all data restored from backups.
Creating non-stripe storage pools that have disk redundancy is always recommended.

To prevent further loss of redundancy or eventual data loss, always replace a failed disk as soon as possible!
TrueNAS can integrate the new disk into the pool, restoring that pool back to full functionality.

## Replacing a Disk

To replace a failed disk, you'll need another disk that has the same or greater capacity.
Any data on the replacement disk will be wiped as part of the process.

The TrueNAS **Dashboard** shows when a pool has been degraded from a failed disk.

<img src="/images/pool-degraded.png">
<br><br>

Click the <i class="fas fa-cog"></i> on the pool's card to go to the status screen for the pool and locate the failed disk.

### Offline the Failed Disk

Clicking <i class="fas fa-ellipsis-v"></i> for the failed disk shows additional operations.

<img src="/images/failed-drive-options.png">
<br><br>

It is recommended to *Offline* the disk before starting the replacement.
This removes the device from the pool and can prevent swap issues.

{{% alert title="Leaving the Disk Online" color="info" %}}
There are some situations where a disk that has not completely failed can be left online to provide additional redundancy during the replacement procedure.
This is not recommended unless the exact condition of the failing disk is known.
Attempting to replace a heavily degraded disk without offlining it first can result in a significantly slower replacement process.
{{% /alert %}}

If the *Offline* operation fails with a "Disk offline failed - no valid replicas" message, go to **Storage > Pools**, click the <i class="fas fa-cog"></i> for the degraded pool, and select *Scrub Pool*.
When the scrub operation is finished, reopen the pool *Status* and try to *Offline* the disk again.

<img src="/images/disk-offline.png">
<br><br>

When the disk status shows as *Offline*, physically remove the disk from the system.
If the replacement disk is not already physically added to the system, add it now.

### Integrating the Replacement Disk into the Pool

In the **Pool Status**, open the options for the *Offline* disk and click *Replace*

<img src="/images/disk-replace.png">
<br><br>

Select a new member disk and click *Replace Disk*.
Remember that the new disk must have the same or greater capacity as the disk being replaced.
If the chosen disk has partitions or data present, the replacement will fail.
To <ins>destroy</ins> any data on the replacement disk and allow the replacement to continue, set the *Force* option.

When the new disk has been wiped and is ready to replace the failed disk, the pool status updates to show the replacement in progress.

<img src="/images/pool-status-replace.png">
<br><br>

TrueNAS resilvers the pool during the replacement process.
For pools with large amounts of data, this can take a long time.

When the resilver is complete, the pool status screen updates to show the new disk and the pool status returns to *Online*.

<img src="/images/pool-status-replace-complete.png">
<br><br>
