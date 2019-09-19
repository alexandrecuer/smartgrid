```
echo.>E:\ssh
```
Copy the default cmdline.txt to cmdline2.txt in the boot partition and then open to edit cmdline.txt, remove: init=/usr/lib/raspi-config/init_resize.sh

```
wget https://raw.githubusercontent.com/openenergymonitor/EmonScripts/master/install/init_resize.sh
chmod +x init_resize.sh
sudo mv init_resize.sh /usr/lib/raspi-config/init_resize.sh
sudo mv /boot/cmdline2.txt /boot/cmdline.txt
sudo reboot

sudo resize2fs /dev/mmcblk0p2
sudo mkfs.ext2 -b 1024 /dev/mmcblk0p3
sudo mkdir /var/opt/emoncms
sudo chown www-data /var/opt/emoncms
wget https://raw.githubusercontent.com/openenergymonitor/EmonScripts/master/defaults/etc/fstab
sudo cp fstab /etc/fstab
sudo reboot
```
install the scripts

```
cd /opt
sudo mkdir openenergymonitor
sudo chown pi:pi openenergymonitor
sudo apt-get install git
cd openenergymonitor
git clone -b master https://github.com/openenergymonitor/EmonScripts
cd EmonScripts
cd install
```

change config.ini with the following lines
```
git_repo[emoncms_core]=https://github.com/alexandrecuer/emoncms.git
emoncms_core_branch=themis
git_repo[config]=https://github.com/alexandrecuer/config.git
git_repo[postprocess]=https://github.com/alexandrecuer/postprocess.git
# emonhub
git_repo[emonhub]=https://github.com/alexandrecuer/emonhub.git
emonhub_branch=modbusTCPinterfacer_multinodes_env_example

symlinked_emoncms_modules[postprocess]=themis

```
launch the scripts
```
./main.sh
```
