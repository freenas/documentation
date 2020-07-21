---
title: "NTP Servers"
description: "Managing NTP Servers"
---

## NTP Server

Go to the **System** ➞ **NTP Servers** page to view, edit, or remove NTP Servers.

<img src="/images/TN-12.0-NTP-1.PNG">
<br><br>


## NTP Server Options

<img src="/images/TN-12.0-NTP-2.PNG">
<br><br>


| Setting  | Value    | Description                                                                                                                                      |
|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| Address  | string   | Enter the hostname or IP address of the NTP server.                                                                                              |
| Burst    | checkbox | Recommended when Max. Poll is greater than 10. Only use on personal servers. Do not use with a public NTP server.                                |
| IBurst   | checkbox | Speed up the initial synchronization, taking seconds rather than minutes.                                                                        |
| Prefer   | checkbox | This option is only recommended for highly accurate NTP servers, such as those with time monitoring hardware.                                    |
| Min Poll | integer  | The minimum polling interval, in seconds, as a power of 2. For example, 6 means 2^6, or 64 seconds. The default is 6, minimum value is 4.        |
| Max Poll | integer  | The maximum polling interval, in seconds, as a power of 2. For example, 10 means 2^10, or 1,024 seconds. The default is 10, maximum value is 17. |
| Force    | checkbox | Force the addition of the NTP server, even if it is currently unreachable.                                                                       |


## Editing a NTP Server

Click on the Options Menu <i class="fa fa-ellipsis-v" aria-hidden="true"></i> and select **Edit**.  Edit as required and click **Save**.

## Deleting a NTP Server


Click on the Options Menu <i class="fa fa-ellipsis-v" aria-hidden="true"></i> and select **Delete**.
