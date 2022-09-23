# Preparing the SD card for the Pi

Here we discuss how to prepare the SD card with the necessary modifications.

## Mount the SD card

We need to identify the disk/partition and then mount in WSL.

```powershell
GET-CimInstance -query "SELECT * from Win32_DiskDrive"
wsl --mount <DiskPath>
```

Then inside the WSL the devices can be used.

```sh
lsblk
blkid /dev/sdx
```

Or mount a single partition?

```powershell
wsl --mount <DiskPath> --partition <PartitionNumber> --type <Filesystem>
```

```sh
sudo dd bs=4M if=2020-02-13-raspbian-buster-lite.img of=/dev/mmcblk0 conv=fsync
```

## References

* Mount a disk in WSL: [link][wsl-mount]
* Flashing the SD card and initial setup: [link][pragmatic-setup]

[wsl-mount]: https://docs.microsoft.com/en-us/windows/wsl/wsl2-mount-disk
[pragmatic-setup]: https://www.pragmaticlinux.com/2020/06/setup-your-raspberry-pi-4-as-a-headless-server/
