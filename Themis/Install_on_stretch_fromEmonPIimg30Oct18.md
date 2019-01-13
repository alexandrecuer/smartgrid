# Install THEMIS tools on the basis of the 30/10/2018 OEM raspbian STRETCH EmonPI img

https://github.com/emoncms/emoncms/blob/master/docs/RaspberryPi/readme.md

Jessie was : https://github.com/emoncms/emoncms/blob/master/docs/RaspberryPi/jessie.md

upgrade from jessie to stretch https://github.com/openenergymonitor/emonpi/wiki/Upgrade-Jessie---Stretch

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
'echo.>D:\ssh
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

////EXPAND FS
create symlink for emonSDexpand
sudo ln -s /home/pi/usefulscripts/sdpart/sdpart_imagefile /sbin/emonSDexpand
emonSDexpand

Nota : if usefulscripts not present 
https://github.com/emoncms/usefulscripts

////PYMODBUS && EMONHUB
sudo apt-get install python-dev
cd /
sudo git clone https://github.com/bashwork/pymodbus
cd pymodbus
sudo python setup.py install

cd /home/pi/emonhub
on change la source du dépôt qui est théoriquement https://github.com/openenergymonitor/emonhub.git
git remote set-url origin https://github.com/alexandrecuer/emonhub.git
sudo git fetch
celà doit faire apparaître la nouvelle branche propre à THEMIS
 * [new branch]      modbusTCPinterfacer_multi_nodes -> origin/modbusTCPinterfacer_multi_nodes

sudo git checkout modbusTCPinterfacer_multi_nodes
sudo service emonhub restart

////EMONCMS
cd /var/www/emoncms

On voit que emoncms utilise les releases (stable) :
git config --list
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
remote.origin.url=https://github.com/emoncms/emoncms.git
remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
branch.stable.remote=origin
branch.stable.merge=refs/heads/stable
branch.master.remote=origin OK
branch.master.merge=refs/heads/master OK
branch.systmdRunner.remote=origin
branch.systmdRunner.merge=refs/heads/systmdRunner

git remote set-url origin https://github.com/alexandrecuer/emoncms.git
sudo git fetch
sudo git checkout master
sudo git pull

////COMPOSER
https://github.com/composer/composer
https://getcomposer.org/download/
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === '93b54496392c062774670ac18b134c3b3a95e5a5e5c8f1a9f115f203b75bf9a129d5daa8ba6a13e2cc8a1da0806388a8') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
sudo php composer-setup.php --install-dir=/sbin --filename=composer
php -r "unlink('composer-setup.php');"

////YARN
curl -o- -L https://yarnpkg.com/install.sh | bash

////DEV-PURPOSES-PHPMYADMIN
on essaye de se connecter à mariadb en invite de commande
mysql -u emoncms -p
on tape le mot de passe : emonpiemoncmsmysql2016 
SHOW DATABASES;
on peut recréer un user root enlevé par OEM 
sudo mysql -e "CREATE USER 'root' IDENTIFIED BY 'emonpimysql2016'; GRANT ALL ON *.* TO 'root'; flush privileges;"

pour créer un user admin
mysql -u admin -p
CREATE USER 'admin'@'%' IDENTIFIED BY 'bbz2xcw';
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%' WITH GRANT OPTION;
FLUSH PRIVILEGES;

pour afficher les users une fois connecté à l'invite mysql
SELECT user, host, plugin FROM mysql.user;

https://github.com/phpmyadmin/phpmyadmin
ni le master ni les dernières release ne sont compatibles avec php7.0
on prend une release compatible de niveau 4.6 et on la décompresse dans /var/www
cd /var/www/phpmyadmin
composer update --no-dev
yarn install
cd /var/www/html
sudo ln -s /var/www/phpmyadmin

le conf de mariadb sont dans etc/mysql
ce conf indique où est le fichier sock
on rajoute dans le config.inc.php de phpmyadmin la ligne suivante :
$cfg['Servers'][$i]['socket'] = '/home/pi/data/mysql/mysql.sock';
il faut aussi rentrer la clé secrête car on s'authentifie par cookie
$cfg['blowfish_secret'] = '123456789012345678901234567890AB';


////DEV-PURPOSES-redis admin
rpi-rw
cd /var/www
sudo git clone https://github.com/ErikDubbelboer/phpRedisAdmin.git
cd phpRedisAdmin/
sudo git clone https://github.com/nrk/predis.git vendor
cd html
sudo ln -s /var/www/phpRedisAdmin
sudo systemctl daemon-reload
sudo service apache2 restart
