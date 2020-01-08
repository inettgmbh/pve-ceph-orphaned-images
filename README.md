# pve-ceph-orphaned-images
Find and display orphaned images on a Proxmox VE Ceph Cluster

pve-ceph-orphaned-images is a tool for finding orphaned images on a Proxmox VE Ceph cluster

Copyright (c) 2018-2020 Marco Gabriel, inett GmbH, https://www.inett.de

This program is free software licensed under AGPLv3.

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

