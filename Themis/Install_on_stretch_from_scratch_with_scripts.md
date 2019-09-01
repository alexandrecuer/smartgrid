# Install Themis on raspbian stretch from scratch using the scripts	

burn a rasbian stretch lite image on the SD using Etcher

open the file /boot/cmdline.txt and remove the last part of the single and only line :
`
init=/usr/lib/raspi-config/init_resize.sh
`
