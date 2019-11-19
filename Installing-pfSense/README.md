# Installation of pfSense on a physical machine
Tools used: 
- Rufus-3.8
- pfSense-2.4.4
#### Table of Contents
- Downloading the image
- Creating Bootable USB

## Configuring a pfSense Bootable USB
#### Download pfSense
Use link: https://www.pfsense.org/download/
##### Image Requirements:
- Architecture: AMD64 (64-bit)
- Installer: USB Memstick Installer 
- Console: Serial (because you are using a USB device)
- Mirror: Will default to closest server
<p align="left">
  <img width="460" height="300" src="https://github.com/Sil3ntSec/pfSense-home-network/blob/master/Images/pfSense.PNG">
</p><br/>

 
#### Creating Bootable USB
Next, you will have to create a bootable USB drive with this pfSense image. I personally like Rufus. Use link: https://rufus.ie/. All of the settings can stay the same within Rufus, but you must specify the device being used and attach the pfSense memstick image
<p align="left">
  <img width="300" height="460" src="https://github.com/Sil3ntSec/pfSense-home-network/blob/master/Images/Rufus1.PNG">
</p>
<div class="paragraph"><p> <br>
 <br></p></div>
 
 #### Booting off of USB
