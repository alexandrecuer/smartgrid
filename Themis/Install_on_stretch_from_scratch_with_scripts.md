# Install Themis on raspbian stretch from scratch using the scripts	

## preparation

On a workstation of any type

burn a rasbian stretch lite image on the SD using Etcher

open the file /boot/cmdline.txt and remove the init= part of the single and only line so that it becomes :

`
dwc_otg.lpm_enable=0 console=serial0,115200 console=tty1 root=PARTUUID=c1dc39e5-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait quiet
`

original full line after the burn

`
dwc_otg.lpm_enable=0 console=serial0,115200 console=tty1 root=PARTUUID=c1dc39e5-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait quiet init=/usr/lib/raspi-config/init_resize.sh
`

enable SSH, assuming the SD has been mouted on the unit E

`
echo.>E:\ssh
`

## installation

plug the SD into the RPI, boot, then connect via SSH (user pi password raspberry)

change user `pi` password, using the command `passwd`

Create a directory named emon in /opt and install git

```
cd /opt
sudo mkdir openenergymonitor
sudo chown pi:pi openenergymonitor
cd openenergymonitor
sudo apt-get install git 
git clone -b master https://github.com/alexandrecuer/EmonScripts
cd EmonScripts
sudo cp init_resize.sh /usr/lib/raspi-config/init_resize.sh
sudo nano /boot/cmdline.txt 
```
just restore the original content with `init=/usr/lib/raspi-config/init_resize.sh` at the end and reboot the pi

Format the new ext2 partition

`
sudo mkfs.ext2 -b 1024 /dev/mmcblk0p3
`

Once done just change the fstab

`
sudo cp /opt/openenergymonitor/EmonScripts/defaults/etc/fstab /etc/fstab
`

Reboot and check partitions types
 
`
sudo file -sL /dev/mmcblk0p*
`
 
or
 
`
lsblk  -f
`
