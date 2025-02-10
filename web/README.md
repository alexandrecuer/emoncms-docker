
use the compose file to run the stack in portainer

you will have 3 containers : web, db and adminer, which is a light version of phpmyadmin

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

## not necessary, just to be sure to understand how things works

connect to the web container and install mariadb-client : `apt-get install mariadb-client`

then connect to the database `mysql -h db --user=emoncms --password=emonpiemoncmsmysql2016`
