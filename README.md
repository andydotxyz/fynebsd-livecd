# fynebsd-livecd [![Build Status](https://api.cirrus-ci.com/github/andydotxyz/furybsd-livecd.svg)](https://cirrus-ci.com/github/andydotxyz/furybsd-livecd)

LiveCD builder for FyneBSD

## Continuous builds

Continuous builds can be downloaded [here](../../releases/continuous/). __CAUTION:__ These are meant for development only. Use at your own risk. Do not use in production environments.

To minimize the amount of data when going from build to build, `.zsync` files are also provided. [More information](https://askubuntu.com/questions/54241/how-do-i-update-an-iso-with-zsync)

It is also possible to directly download and write straight to a USB stick in one go. __Caution:__ This will OVERWRITE the entire contents of the USB stick.

```
root@FreeBSD:/ # umount /dev/daX*
root@FreeBSD:/ # curl -L "https://github.com/andydotxyz/furybsd-livecd/releases/download/continuous/FyneBSD-12.1.iso" | dd of=/dev/daX bs=4m
```

## System Requirements for building LiveCD

* 2 GHz dual core processor
* 4 GiB RAM (system memory)
* 50 GB of hard-drive space
* Either a CD-RW/DVD-RW drive or a USB port for writing the installer media
* FreeBSD 12.1-RELEASE or later

## System Requirements for using LiveCD

* 2 GHz dual core processor
* 4 GiB RAM (system memory for physical and viritualized installs)
* VGA capable of 1024x768 screen resolution 
* Either a CD/DVD drive or a USB port for booting the installer media

## Customize (optional)

Add more packages to FyneDesk edition:
```
edit settings/packages.fynedesk
```

Enable more services:
```
edit settings/rc.conf.fynedesk
```

## Build a new release 
Generate an ISO with FyneDesk:
```
./build.sh
```

## Burn

Burn the image to DVD:

```
pkg install cdrtools
cdrecord /usr/local/furybsd/iso/FyneBSD-12.1.iso
```

Write the image to USB stick:
```
sudo dd if=/usr/local/furybsd/iso/FyneBSD-12.1.iso of=/dev/daX bs=4m status=progress
```

## Credentials for live media

There is no password for `liveuser`. The `liveuser` account is removed upon install.  There is also no root password until it is set in the installer.

