# Installation of pfSense on a physical machine 
Tools used: 
- Rufus-3.8 
- pfSense-2.4.4
#### Table of Contents
- <a class="btn btn-primary" href="https://github.com/Sil3ntSec/pfSense-home-network/tree/master/Installing-pfSense#configuring-a-pfsense-bootable-usb" role="button">Configuring a pfSense Bootable USB</a>
  - <a class="btn btn-primary" href="https://github.com/Sil3ntSec/pfSense-home-network/tree/master/Installing-pfSense#download-pfsense" role="button">Downloading the Image</a>
  - <a class="btn btn-primary" href="https://github.com/Sil3ntSec/pfSense-home-network/tree/master/Installing-pfSense#creating-bootable-usb" role="button">Creating Bootable USB</a>
    - <a class="btn btn-primary" href="https://github.com/Sil3ntSec/pfSense-home-network/tree/master/Installing-pfSense#image-requirements" role="button">Image Requirements</a>
  - <a class="btn btn-primary" href="https://github.com/Sil3ntSec/pfSense-home-network/tree/master/Installing-pfSense#booting-off-of-a-usb" role="button">Booting off of a USB</a>
  - <a class="btn btn-primary" href="https://github.com/Sil3ntSec/pfSense-home-network/tree/master/Installing-pfSense#performing-a-full-install-of-pfsense" role="button">Performing a Full install of pfSense</a>
- <a class="btn btn-primary" href="https://github.com/Sil3ntSec/pfSense-home-network/tree/master/Installing-pfSense#configuring-pfsense" role="button">Configuring pfSense</a>

## Configuring a pfSense Bootable USB
#### Download pfSense
Use link: https://www.pfsense.org/download/
##### Image Requirements:
- **Architecture:** AMD64 (64-bit)
- **Installer:** USB Memstick Installer 
- **Console:** Serial (because you are using a USB device)
- **Mirror:** Will default to the closest mirror to your location
<p align="left">
  <img width="460" height="300" src="https://github.com/Sil3ntSec/pfSense-home-network/blob/master/Images/pfSense.PNG">
</p><br/>

#### Creating Bootable USB
The downloaded image must be written to target media before it can be used We will have to write the installer ISO to a USB device. A tool that I personally like is Rufus. Use link: https://rufus.ie/. All of the settings can stay the same within Rufus, but you must specify the device being used and attach the pfSense memstick image under 'Boot Selection'.
<p align="left">
  <img width="300" height="460" src="https://github.com/Sil3ntSec/pfSense-home-network/blob/master/Images/Rufus1.PNG">
</p><br/>

#### Booting off of a USB
Plug the USB into the physcial machine you want to install pfSense on and navigate to the boot menu. This will include using one of these keys during bootup: Esc, F2, F10 or F12 (depending on the manufacture of your motherboard). You might have to disable *Secure Boot* to allow your machine to boot from the USB. The boot menu will look identical to the one below, but will include a bootable device labeled USB. Select the pfSense bootable drive and pfSense will start.
<p align="left">
  <img width="460" height="300" src="https://github.com/Sil3ntSec/pfSense-home-network/blob/master/Images/bootmenu1.jpg">
</p><br/>

#### Performing a Full Install of pfSense
As the operating system boots and pfSense starts, a wizard will start and prompt you with copyright and distribution information. Select 'Accept'.
<p align="left">
  <img width="560" height="300" src="https://github.com/Sil3ntSec/pfSense-home-network/blob/master/Images/pfSense1.png">
</p>

To start the installation, select 'OK' while the 'Install' option is selected.
<p align="left">
  <img width="560" height="300" src="https://github.com/Sil3ntSec/pfSense-home-network/blob/master/Images/pfSense2.png">
</p>

Next, is to select the filesystem that will be used. By defualt, UFS is selected (this option is best for beginners). Select 'OK' to continue. This will configure the hard drive. 
<p align="left">
  <img width="560" height="300" src="https://github.com/Sil3ntSec/pfSense-home-network/blob/master/Images/pfSense3.png">
</p>

This step allows you to choose the keymap selection. The defualt keymap is US standard. Select your keymap and continue.
<p align="left">
  <img width="560" height="300" src="https://github.com/Sil3ntSec/pfSense-home-network/blob/master/Images/pfSense4.png">
</p>

Finally onto the installation of pfSense, after selecting your keymap, the target disk will get wiped and begin installing pfSense. Copying files may take some time to finish.
<p align="left">
  <img width="560" height="300" src="https://github.com/Sil3ntSec/pfSense-home-network/blob/master/Images/pfSense7.png">
</p>

After the installation is complete, there will be a prompt to manually make any modifications, select 'No' to continue.
<p align="left">
  <img width="560" height="300" src="https://github.com/Sil3ntSec/pfSense-home-network/blob/master/Images/pfSense5.png">
</p>

Now that pfSense is installed, the machine must reboot so that pfSense may start from the target disk. Select 'Reboot' and then press Enter. Be sure to remove the USB device so that the machine will boot from the hard drive.
<p align="left">
  <img width="560" height="300" src="https://github.com/Sil3ntSec/pfSense-home-network/blob/master/Images/pfSense6.png">
</p>
Now it's time to configure the interfaces within your new pfSense machine!<br/>

## Configuring pfSense
After the pfSense machine reboots, the machine will boot into the newly installed operating system. By default, pfSense will pick an interface to set-up as the WAN interface with DHCP and leave the LAN interface unconfigured. The WAN interface will aquire an IP address within the subnet your internet provider assigned. 
<p align="left">
  <img width="560" height="300" src="https://github.com/Sil3ntSec/pfSense-home-network/blob/master/Images/pfSense9.jpg">
</p><br/>

#### Configuring LAN Interface
If you installed pfSense on an extra desktop that was laying around, you must make sure that the desktop has two ethernet ports. For my build, I installed an extra ethernet port using a PCIe slot within my motherboard, that wa $12. It doesn't matter which port your LAN or WAN is connected to. 
##### One by One steps:
1. Assigning interfaces
2. Configuring interfaces
3. Configuring the LAN interface
4. IPv4 address to LAN
5. Subnet bit count
6. IPv4 upstream gateway address
7. IPv6 address
8. DHCP on the LAN interface
9. Revert to HTTP as the webConfigurator protocol
10. Save the configurations for the LAN interface

