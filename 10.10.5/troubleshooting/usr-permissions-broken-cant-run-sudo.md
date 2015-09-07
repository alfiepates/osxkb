User can't run sudo due to broken `/usr` permissions
==============================================================

Issue
-----
When setting the permissions of a file using Finder, it's possible to accidentally change the setuid bit of the file. If the setuid but of `/usr` isn't 0, sudo will refuse to run.

Solution
--------

Boot into a known-good OS X installation, either from a USB drive or by connecting the broken disk to another machine (this can be achieved using Target Disk Mode on Macs with non-removable drives). Then, run the following command where `/Volumes/BrokenPermsDisk` is the mountpoint of the disk with broken permissions.

```bash
sudo diskutil repairPermissions /Volumes/BrokenPermsDisk
```
