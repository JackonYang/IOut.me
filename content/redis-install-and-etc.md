## Redis -- Install and Config 


#### 安装

```shell
#!/bin/bash
set -e

wget http://download.redis.io/releases/redis-stable.tar.gz
tar xzf redis-stable.tar.gz
cd redis-stable/
make
sudo make install
```


#### 配置

```
port=6379

sudo mkdir -p /etc/redis
sudo cp redis.conf /etc/redis/$port.conf

# start after system reboot
sudo cp utils/redis_init_script /etc/init.d/redis_$port
sudo mkdir -p /var/redis/$port
sudo update-rc.d redis_$port defaults
```

修改 /etc/redis/6379.conf

```shell
daemonize yes  # !important
pidfile /var/run/redis_6379.pid
port 6379
dbfilename dump.rdb
dir /var/redis/6379  # !important
```