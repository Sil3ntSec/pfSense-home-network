# Installation of pfSense on a physical box
Tools used: 
- Rufus-3.8
- pfSense-2.4.4

## Configuring a pfSense Bootable USB
#### Downloading the Image
The pfSense image must be the memstick version, along with the .img.gz file type as shown: **pfSense-CE-memstick-2.4.4-RELEASE-amd64.img.gz**. Use link: https://www.pfsense.org/download/
<p align="left">
  <img width="460" height="300" src="https://github.com/Sil3ntSec/pfSense-home-network/blob/master/Images/pfSense1.PNG">
</p>
<div class="paragraph"><p> <br>
 <br></p></div>
 
### Creating Bootable USB
Next, you will have to create a bootable USB drive with this pfSense image. I personally like Rufus. Use link: https://rufus.ie/. All of the settings can stay the same within Rufus, but you must specify the device being used and attach the pfSense memstick image
<p align="left">
  <img width="300" height="460" src="https://github.com/Sil3ntSec/pfSense-home-network/blob/master/Images/Rufus1.PNG">
</p>
