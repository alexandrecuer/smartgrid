# Install THEMIS tools on the basis of the 30/10/2018 OEM raspbian STRETCH EmonPI img

https://github.com/emoncms/emoncms/blob/master/docs/RaspberryPi/readme.md

Jessie was : https://github.com/emoncms/emoncms/blob/master/docs/RaspberryPi/jessie.md

upgrade from jessie to stretch https://github.com/openenergymonitor/emonpi/wiki/Upgrade-Jessie---Stretch

Check also this : https://github.com/openenergymonitor/emonpi/wiki/emonSD-pre-built-SD-card-Download-&-Change-Log

just for general knowledge : https://anton.logvinenko.site/en/blog/how-to-install-redis-and-redis-php-client.html

## enabling SSH
Insert the microSD in a SD adapter and plug it in the reader of the laptop (we assume the laptop running Microsoft window)
Make sure that the SD adapter is in write mode (grey latch upwards)

Press Windows Key and r at the same time and then type :
```
cmd
```
At the MSDOS prompt:
```
echo.>D:\ssh
```

# NODERED
``
bash <(curl -sL https://raw.githubusercontent.com/node-red/raspbian-deb-package/master/resources/update-nodejs-and-nodered)
``
<br>
``
mv /home/pi/.node-red ~/data/node-red
``
<br>Create Symlink
``
sudo ln -s /home/pi/data/node-red /home/pi/.node-red
``

To start nodered as a service:
``sudo systemctl enable nodered.service``


- activate projects ``sudo nano /home/pi/data/node-red/settings.js`` in the editorTheme section :
```
projects: {enabled: true}
```



## UPDATE & UPGRADE
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
after that mariadb could not want to start
```
sudo nano /lib/systemd/system/mariadb.service
```
Change``ProtectHome=true`` to ``ProtectHome=false``

Then reload
```
sudo systemctl daemon-reload
sudo service mariadb start
sudo shutdown -r now
```

## EXPAND FS
create symlink for emonSDexpand
``sudo ln -s /home/pi/usefulscripts/sdpart/sdpart_imagefile /sbin/emonSDexpand``
```
emonSDexpand
```
Nota : if usefulscripts not present 
https://github.com/emoncms/usefulscripts

## PYMODBUS
```
sudo apt-get install python-dev
cd /
sudo git clone https://github.com/bashwork/pymodbus
cd pymodbus
sudo python setup.py install
```
## EMONHUB
```
cd /home/pi/emonhub
```
change the source repository which should be : https://github.com/openenergymonitor/emonhub.git
```
git remote set-url origin https://github.com/alexandrecuer/emonhub.git
sudo git fetch
```
You should see a new branch called THEMIS
```
 * [new branch]      modbusTCPinterfacer_multi_nodes -> origin/modbusTCPinterfacer_multi_nodes
```
```
sudo git checkout modbusTCPinterfacer_multi_nodes
sudo service emonhub restart
```
## EMONCMS
```
cd /var/www/emoncms
```

Emoncms team uses releases (stable) :
```
git config --list
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
remote.origin.url=https://github.com/emoncms/emoncms.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.stable.remote=origin
branch.stable.merge=refs/heads/stable
branch.master.remote=origin
branch.master.merge=refs/heads/master
branch.systmdRunner.remote=origin
branch.systmdRunner.merge=refs/heads/systmdRunner
```
```
git remote set-url origin https://github.com/alexandrecuer/emoncms.git
sudo git fetch
sudo git checkout master
sudo git pull
```

## COMPOSER
https://github.com/composer/composer

https://getcomposer.org/download/
```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
```
``
php -r "if (hash_file('sha384', 'composer-setup.php') === '93b54496392c062774670ac18b134c3b3a95e5a5e5c8f1a9f115f203b75bf9a129d5daa8ba6a13e2cc8a1da0806388a8') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
``
```
sudo php composer-setup.php --install-dir=/sbin --filename=composer
```
```
php -r "unlink('composer-setup.php');"
```


## YARN
```
curl -o- -L https://yarnpkg.com/install.sh | bash
```

## DEV-PURPOSES-PHPMYADMIN

Please note that root tcpip access to mariadb is disabled for security purposes

default root password is emonpimysql2016

default emoncms password is emonpiemoncmsmysql2016

You should change them and report the changes for the user emoncms in the settings.php file of Emoncms

to connect localy to mariadb ``mysql -u emoncms -p`` or ``mysql -u root -p``

https://github.com/phpmyadmin/phpmyadmin

STRETCH runs PHP7.0 and phpmyadmin master branch is for PHP7.1 or above

Dowload a release compatible with PHP7.0 (v4.6..) and unzip in /var/www

```
cd /var/www/phpmyadmin
composer update --no-dev
yarn install
cd /var/www/html
sudo ln -s /var/www/phpmyadmin
```

mariadb conf files are in /etc/mysql

this configuration indicates where is the sock file

Create a config.inc.php file from the config.sample.inc.php, and modify as following :
```
$cfg['blowfish_secret'] = '123456789012345678901234567890AB';
```

```
$i = 0;

/**
 * First server
 */
$i++;
/* Authentication type */
$cfg['Servers'][$i]['auth_type'] = 'cookie';
$cfg['Servers'][$i]['socket'] = '/home/pi/data/mysql/mysql.sock';
/* Server parameters */
$cfg['Servers'][$i]['host'] = 'localhost';
$cfg['Servers'][$i]['connect_type'] = 'socket';
$cfg['Servers'][$i]['compress'] = false;
$cfg['Servers'][$i]['AllowNoPassword'] = false;
```
Access is done via cookies and not with the old config mode

## DEV-PURPOSES-redis admin

```
cd /var/www
sudo git clone https://github.com/ErikDubbelboer/phpRedisAdmin.git
cd phpRedisAdmin/
sudo git clone https://github.com/nrk/predis.git vendor
cd /var/www/html
sudo ln -s /var/www/phpRedisAdmin
sudo systemctl daemon-reload
sudo service apache2 restart
```
