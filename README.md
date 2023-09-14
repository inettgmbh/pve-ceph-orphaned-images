# pve-ceph-orphaned-images
Find and display orphaned images on a Proxmox VE Ceph Cluster

pve-ceph-orphaned-images is a tool for finding orphaned images on a Proxmox VE Ceph cluster

Copyright (c) 2018-2020 Marco Gabriel, inett GmbH, https://www.inett.de

This program is free software licensed under AGPLv3.

## Purpose

Sometimes when disk images are moved or VMs are removed from the cluster, a Ceph disk images still has some watchers. This means, that the image can't be removed at the moment and you should try again later when all watchers are gone. If this happens frequently because a cluster runs for a few years, there may be a collection of old, outdated images that aren't used anymore and just waste some space on your Ceph storage. Proxmox VE shows only images that are defined in a VM/CT configuration. So it is a cumbersome process to list all images in a Ceph cluster and compare them manually with your existing VM configurations if they are still being used.

## Usage

Just run the script by typing `pve-ceph-orphaned-images` and the script lists RBD images in your ceph pools that are not used in any VM configurations. It works for both KVM and LXC machines and scans all pools within ceph.

## Example

1. run the script
```
root@pve:~# ./pve-ceph-orphaned-images
```

2. see the results
```
ceph_kvm/fio_test  1GiB
ceph_kvm/vm-101-disk-0  50GiB
ceph_kvm/vm-102-disk-0  32GiB
ceph_kvm/vm-103-state-MDCreinstall_ESETLog  16GiB
ceph_kvm/vm-105-disk-1  500GiB
ceph_kvm/vm-105-disk-2  50GiB
ceph_kvm/vm-105-disk-3  50GiB
ceph_kvm/vm-110-disk-0  100GiB
ceph_kvm/vm-119-disk-1  32GiB
ceph_kvm/vm-119-disk-2  15GiB
ceph_kvm/vm-119-disk-3  15GiB
ceph_kvm/vm-119-disk-4  100GiB
ceph_kvm/vm-119-disk-5  100GiB
ceph_lxc/vm-119-disk-1  16GiB
ceph_lxc/vm-123-disk-0  8GiB
ceph_lxc/vm-164-disk-0  100GiB
backup/vm-127-disk-0  100GiB
backup/vm-128-disk-1  9.8TiB
```

3. check the images manually and move them away to regain free space on your ceph

