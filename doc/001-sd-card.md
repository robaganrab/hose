# Preparing the SD card for the Pi

Here we discuss how to prepare the SD card with the necessary modifications.

We start from an official image. If more customization is needed or
multiple devices are managed, an own image might worth the effort.

Fortunately we don't have to go very deeply into technical stuff
as there is the [Raspberry Pi Imager][rpi-imager].
If we had to, it would be harder as Windows 11 is needed
or some other virtualization solution.

## Download the Raspberry Imager

[Download page][rpi-imager].

## Flash the SD card

Select 64 bit Lite version in the "More" part.
Select the SD card.
Change settings:

* Enable SSH.
* Add ssh key (eg. ~/.ssh/id_rsa.pub) with which you plan to connect.
* Change default user name for security.
* Optionally configure WLAN.
* Set locale.

Write the image and configuration.

## Try the shiny new Raspberry OS

Once the writing finishes, try it in the Raspberry.
It should be accessible via ssh.
It helps a lot if a known, fixed IP is assigned in the home router.

## References

* Raspberry Imager: [link][rpi-imager]
* Microsoft's explanation how to mount in WSL2: [link][wsl2-mount-disk]

[rpi-imager]: https://downloads.raspberrypi.org/imager/imager_latest.exe
[wsl2-mount-disk]: https://learn.microsoft.com/en-us/windows/wsl/wsl2-mount-disk
