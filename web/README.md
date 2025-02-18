# how to build

```
docker build --build-arg="BUILD_FROM=php:8.2.27-apache" -t emoncms_legacy_docker .
```

# how to use

From this folder, initialize the /emoncms_conf folder
```
sudo mkdir /emoncms_conf
sudo chown $USER /emoncms_conf/
cp -R -f emoncms_conf /
```

use the compose file to run the stack in portainer

you will have 4 containers : web, db, mqtt and adminer, which is a light version of phpmyadmin

connect to adminer and create the emoncms database, then the emoncms user which you grant the rights on the stack network, here 172.22.0.*

```
CREATE USER 'emoncms'@'172.22.0.%' IDENTIFIED BY 'emonpiemoncmsmysql2016';
GRANT ALL ON emoncms.* TO 'emoncms'@'172.22.0.%';
flush privileges;
```
of course, you can secure things like that :

```
DELETE FROM mysql.user WHERE User='root' AND Host NOT IN ('localhost', '127.0.0.1', '::1');
```

connect to the mqtt container and replace username and password by what you want, so to be secure :

```
mosquitto_passwd -b /etc/mosquitto/passwd "emonpi" "emonpimqtt2016"
```
restart the mqtt container in order to activate credentials

to interrogate the broker, there is a really super tool called [MQTT explorer](http://mqtt-explorer.com/) : if you are beginning with all those iot stuff, use it !

to connect, use the credentials, 127.0.0.1 for the host and 2883 for the port

## not necessary, just to be sure to understand how things works

connect to the web container and install mariadb-client : `apt-get install mariadb-client`

then connect to the database `mysql -h db --user=emoncms --password=emonpiemoncmsmysql2016`

