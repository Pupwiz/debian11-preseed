# Debian 12  Bookworm fully automatic install through ISO remastering
Script and configuration to remaster a debian netinst ISO for 100% unattended install

Pulls current net install iso from Debian site automatically and adds custom preseed.

Usage:

1. Adapt the preseed.cfg file to your needs. (This one installs just SSH and sudo)
2. Run:
```
./make-preseed-iso.sh 
```
This will create a new ISO image named `preseed-debian-(version-amd64)-netinst.iso` that
installs debian on the first available disk without intervention, not even a boot menu prompt.

### WARNING: This deletes stuff!

The preseed.cfg that in this repository ***completely erases the first disk\*\****

> ** as returned by `list-devices disk`, excluding usb

Also... open the script and read what it does. I made this for myself because I'm tired of hitting
enter 40 times everytime I need to install debian.

The location of the initrd is hardcoded to 'install.amd', this needs to be changed if you are using an iso
for other than amd64.

The configuration for the boot menu options is specific to bullseye in the case of a UEFI system because grub uses the position of the entry to specify the default option.

### More on how to preseed
* https://wiki.debian.org/DebianInstaller/Preseed
* https://wiki.debian.org/DebianInstaller/Preseed/EditIso
* https://wiki.debian.org/RepackBootableISO
