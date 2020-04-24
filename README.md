# 📦 Nextcloud config for docker-compose

It currently uses MariaDB as database. And memcache Redis ready.

### Usage

1. Edit `docker-compose.yaml` replace [FILL_HERE] fields with meaningfull values.
2. Run `docker-compose up -d`
3. Run `docker-compose stop`
4. `cd data/app/config` and edit `config.php`
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

5. Run `docker-compose start` again

### Enable UTF8 support for MariaDB

Folow the instructions mentioned [here](https://docs.nextcloud.com/server/12/admin_manual/configuration_database/mysql_4byte_support.html)
