---
title: "Developer's Notes"
description: "Running updates about TrueNAS SCALE Nightly status and current issues."
---

#### Recent Updates
> 7/16/2020 - [Slack Instance](https://www.ixsystems.com/community/threads/collaborator-community-slack-instance.85717/) is available for community contributors

> 7/15/2020 - VM support using KVM as the backend has arrived, including support for PCI passthrough and nested virtualization.

## System Requirements

- Any x86_64 compatible (Intel or AMD) processor
- 8GB of RAM (More is better)
- 20GB Boot Device


## Nightly Status

Nightly images for TrueNAS SCALE are built every 24 hours, at around 2AM Eastern (EDT/EST) time. Online updates are created every 2 hours and can be used via the UI's online updating page.

ISO's can be downloaded here:

[https://www.truenas.com/download-truenas-scale/](https://www.truenas.com/download-truenas-scale/ "https://www.truenas.com/download-truenas-scale/")


## Current Feature Status

The nightly images are very much a WIP until we get farther along in our development process. They should be suitable for very adventerous users and developers who are not afraid to use the command-line in some instances.


**Supported via the UI:**
- Pool creation
- Pool Management
- Samba Shares
- iSCSI Shares
- AFP Shares
- NFS Shares
- AD / LDAP Directory Services
- Online / Offline updating
- Virtual Machines

**Supported via the CLI (Currently)**
- Docker
- Docker with NVIDIA --gpu passthrough flags
- Gluster
- Wireguard

**TODO**

- Posix NFSv4 ACLs
- Docker UI
- Clustered Datasets API support for TrueCommand
- TrueCommand Clustering UI for SCALE


## Virtual Machines

**PCI Passthrough Devices**

In order to use PCI passthrough devices with VM's, following steps should be followed so that the PCI devices shows up in UI when we want to create a PCI device to be attached to a VM.

1) Identify the PCI device which should be used for passthrough with command `virsh nodedev-list pci`.
2) Once PCI address has been identified, it should be made sure that the host OS is not using the device anywhere i.e pools etc. After ensuring this case, please  execute `virsh nodedev-detach pci_0000_26_00_0` where `pci_0000_26_00_0` is the name of the PCI device.
3) Step (2) will detach the PCI device from the host and it can be used with a VM guest by adding a PCI device in a VM via UI.

The above steps should be performed when there has been at least 1 VM created via UI.
Please ensure that the device an be safely used with the guest as if it's for example part of a CPU and we try to pass it through to the guest, that might result in a crash and the system will only recover after a reboot.
