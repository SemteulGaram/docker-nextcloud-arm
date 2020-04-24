# 📦 Nextcloud config for docker-compose

It currently uses MariaDB as database. And memcache Redis ready.

### Usage

1. Edit `docker-compose.yaml` replace [FILL_HERE] fields with meaningfull values.
  - more environments option in [https://github.com/nextcloud/docker](https://github.com/nextcloud/docker)
2. Run `docker-compose up -d`
3. Open browser `localhost:9080` on host machine
4. Initialize Nextcloud with `MySQL/MariaDB` database host: `nextcloud-mariadb:3306`
5. Wait installer finish
6. Run `docker-compose stop`
7. `cd data/app/config` and edit `config.php` (WARNING: If the entries already exist, there is no need to edit them!)
```
  'memcache.local' => '\\OC\\Memcache\\APCu',
```
to
```
  'memcache.local' => '\\OC\\Memcache\\APCu',
  'memcache.distributed' => '\\OC\\Memcache\\Redis', # If you need distributed server
  'memcache.locking' => '\\OC\\Memcache\\Redis',
  'redis' => array(
    'host' => getenv('REDIS_HOST'),
    'password' => getenv('REDIS_PORT'),
  ),
```
... and other config you need.

8. Run `docker-compose start` again
9. Profit?

### Enable UTF8 support for MariaDB

Folow the instructions mentioned [here](https://docs.nextcloud.com/server/12/admin_manual/configuration_database/mysql_4byte_support.html)

### Useful tips
```
# config.php

'simpleSignUpLink.shown' => false # Hide free signup message
```
