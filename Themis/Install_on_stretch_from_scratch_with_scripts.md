# Install Themis on raspbian stretch from scratch using the scripts	

burn a rasbian stretch lite image on the SD using Etcher

open the file /boot/cmdline.txt and remove the init= part of the single and only line so that it becomes :

`
dwc_otg.lpm_enable=0 console=serial0,115200 console=tty1 root=PARTUUID=c1dc39e5-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait quiet
`

original full line after the burn
`
dwc_otg.lpm_enable=0 console=serial0,115200 console=tty1 root=PARTUUID=c1dc39e5-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait quiet init=/usr/lib/raspi-config/init_resize.sh
`
