This is a record for my attempt of installing Linux on Winbook TW102.
# Hardware

Winbook TW102 is an inexpensive Intel Atom based tablet sold by
[Micro Center](https://www.microcenter.com/product/496688/winbook-tw102-101-quot) with Windows 10 Home 32 bit preinstalled.

Features of Winbook TW102:
* Intel Atom x-5 Z8350 processor 1.44 GHz
* 2GB LP-DDR3 RAM
* 32GB eMMC Storage
* 10.1" 1280x800 IPS Touch Display
* 802.11b/g/n Wireless
* Bluetooth
* Micro-SD card reader
* 6000 mAh Lithium battery

It is recommended that buying the separately sold compatible keyboard makes it much easier to use Linux on it.

# Linux Installation

## System Recovery Drive
This tablet has only 32 GB storage so I suggest wiping out the preinstalled Windows 10 before installing Linux. It is simply
too restrictive for a dual boot. So before installing Linux, it is recommended to backup your personal data in
Windows 10. Find a USB drive of 8 - 16 GB and create a recovery drive to the USB drive in case you need to reinstall
Windows 10. Note that in Windows you can link your license to your Microsoft account as a digital license so you don't need
to enter your product key for Windows 10 reinstallation.

## Creating Linux Installation USB Drive
One caveat is that Winbook TW102 processor supports 64 bit instructions but the UEFI firmware is 32 bit. To install a 64 bit
Linux system you need multiarch installation files. I used the Debian Buster multiarch CD image. Use a working Linux
computer and follow the official Debian instructions to create the Debian installation USB drive.

## Enter BIOS and Change Boot Order
If you don't have the compatible Winbook TW102 keyboard then you need to plug a USB hub and a USB keyboard. Plug the Linux
installation USB drive into the tablet USB port. Power off the tablet. Power on the tablet by pressing the
power button and then immediately press the DEL key to enter BIOS settings. Change the boot order and set the USB drive as
the first booting device. Save and exit.

## GRUB Menu and Orientation Issue
The tablet should boot from the USB drive now. GRUB menu is displayed but distorted and non-readable. Just press Enter key
and you will proceed to the graphical installation dialogs. By default, the display is in portrait mode. It is suggested
that adding kernel parameters can force it in horizontal mode.

## Touchpad and Network Issue
The touchpad is not working in the installation. You can either just use the keyboard to navigate or plug in a USB mouse.
During the network configuration, the WiFi does not work even you have the required non-free firmware and access points
can be
scanned and displayed. It just fails to configue the wireless network after entering the WPA passphrase. It might work
if there is an open access point but I have not tried. So I used a USB to Ethernet adapter instead and it successfully
detected the wired network and the rest of the installation goes smoothly. When selecting Desktop environment, it is
recommended to use a lightweight desktop manager such as Xfce as this tablet is a low end product.

# Post Installation
## Things Work
Note that I used the unofficial Debian installation CD image with non-free firmware built in. If you use the official CD
image then you probably need to add non-free firmware for some of the components.
* Intel Graphics work out of the box. By default it uses the portrait mode. In a terminal run
`xrandr --output DSI-1 --rotate right` to switch to the horizontal mode.
* Touchpad mostly works but I could not find the tap to click option in the touchpad settings.
* WiFi works out of the box.
* Audio works out of the box.
## Things Don't Work
* Touchscreen
* Cameras
