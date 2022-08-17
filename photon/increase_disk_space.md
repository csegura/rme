# Expand disk

Expand disk from vmware & enable rescan

```
echo 1 > /sys/class/block/sda/device/rescan


#fdisk -l
Disk /dev/sda: 16 GiB, 17179869184 bytes, 33554432 sectors
Disk model: Virtual disk
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 42D050AC-C84E-44B3-9B38-E11A40908271

Device     Start      End  Sectors Size Type
/dev/sda1   2048    10239     8192   4M BIOS boot
/dev/sda2  10240    30719    20480  10M EFI System
/dev/sda3  30720 33554398 33523679  16G Linux filesystem

#df -h
Filesystem      Size  Used Avail Use% Mounted on
devtmpfs        4.0M     0  4.0M   0% /dev
tmpfs           2.0G     0  2.0G   0% /dev/shm
tmpfs           790M  916K  789M   1% /run
tmpfs           4.0M     0  4.0M   0% /sys/fs/cgroup
/dev/sda3        16G  9.8G  5.1G  67% /
tmpfs           2.0G   11M  2.0G   1% /tmp
/dev/sda2        10M  2.0M  8.1M  20% /boot/efi
tmpfs           395M     0  395M   0% /run/user/0
overlay          16G  9.8G  5.1G  67% /var/lib/docker/overlay2/dd12ee4d04dba6971d053f2a88b2f0e98fc038f62cf72911f4bc439f46fa5942/merged
overlay          16G  9.8G  5.1G  67% /var/lib/docker/overlay2/777b55779153282adb78bda4c21640659a4eeae30961b00d7aca06fa55314175/merged
overlay          16G  9.8G  5.1G  67% /var/lib/docker/overlay2/366199275c6489e96a83dc13bdd91ad49746ad689a249bc3163ce65d429ef015/merged

```

Install parted
```
tdnf install parted



```
