# Compare object storage to block storage and explain which one is preferable when available

### Official Docker Documentation
[Section 'Other considerations' in chapter 'Select a storage driver'](https://docs.docker.com/engine/userguide/storagedriver/selectadriver/#other-considerations)


Ideally, very little data is written to a container’s writable layer, and you use Docker volumes to write data. However, some workloads require 
you to be able to write to the container’s writable layer. This is where storage drivers come in.

In the container world we use two types of filesystems: overlays and snapshotting filesystems. AUFS and OverlayFS are overlay filesystems which have multiple directories with file diffs for each “layer” in an image. Snapshotting filesystems include devicemapper, btrfs, and ZFS which handle file diffs at the block level. Overlays usually work on common filesystem types such as EXT4 and XFS whereas snapshotting filesystems only run on volumes formatted for them.

Docker supports the following storage drivers:

- **overlay2** is the preferred storage driver, for all currently supported Linux distributions, and requires no extra configuration.
- **aufs** is the preferred storage driver for Docker 18.06 and older, when running on Ubuntu 14.04 on kernel 3.13 which has no support for overlay2.
- **devicemapper** is supported, but requires direct-lvm for production environments, because loopback-lvm, while zero-configuration, has very poor performance. devicemapper was the recommended storage driver for CentOS and RHEL, as their kernel version did not support overlay2. However, current versions of CentOS and RHEL now have support for overlay2, which is now the recommended driver. The devicemapper driver uses block devices dedicated to Docker and operates at the block level, rather than the file level.
- The **btrfs** and **zfs** storage drivers are used if they are the backing filesystem (the filesystem of the host on which Docker is installed). These filesystems allow for advanced options, such as creating “snapshots”, but require more maintenance and setup. Each of these relies on the backing filesystem being configured correctly.
- The **vfs** storage driver is intended for testing purposes, and for situations where no copy-on-write filesystem can be used. Performance of this storage driver is poor, and is not generally recommended for production use.