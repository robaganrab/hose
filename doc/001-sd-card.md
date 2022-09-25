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
RPOS_BASE_URL="https://downloads.raspberrypi.org/raspios_lite_arm64/images/" && \
RPOS_DIR_URL="${RPOS_BASE_URL}$(curl --silent "${RPOS_BASE_URL}" | perl -lane 'm!a href="(raspios_lite_arm64-\d+-\d+-\d+/)"! && print $1' | sort | tail -1)" && \
RPOS_COMPRESSED_FILE="$(curl --silent "${RPOS_DIR_URL}" | perl -lane 'm!a href="(\d{4}-\d{2}-\d{2}-raspios.*?arm64-lite.*?.xz)"! && print $1' | sort | tail -1)" && \
curl --progress-bar --remote-name "${RPOS_DIR_URL}${RPOS_COMPRESSED_FILE}" --remote-name "${RPOS_DIR_URL}${RPOS_COMPRESSED_FILE}.sha256" && \
( sha256sum -c "${RPOS_COMPRESSED_FILE}.sha256" || \
    echo "Checksum failed!" >&2 ) && \
( xz --decompress "${RPOS_COMPRESSED_FILE}" || \
    echo "Decompress failed" >&2 ) && \
RPOS_IMAGE_FILE="${RPOS_COMPRESSED_FILE%.*}" && \
echo "Flashing ${RPOS_IMAGE_FILE} to SD card" >&2  && \
sudo dd bs=4M if="${RPOS_IMAGE_FILE}" of="${SD_PARTITION}" conv=fsync
```

## References

* Mount a disk in WSL: [link][wsl-mount]
* Flashing the SD card and initial setup: [link][pragmatic-setup]

[wsl-mount]: https://docs.microsoft.com/en-us/windows/wsl/wsl2-mount-disk
[pragmatic-setup]: https://www.pragmaticlinux.com/2020/06/setup-your-raspberry-pi-4-as-a-headless-server/
