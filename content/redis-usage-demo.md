# 常见 Redis 使用场景 Demo

缓存 ｜ 爬虫 ｜ 消息管道

## 什么是 Redis？

官网的回答是：

	Redis is an open source (BSD licensed), in-memory data structure store, used as database, cache and message broker

基于内存的“数据结构”存储，可以用作：

- 数据库
- 缓存
- 消息管道

我们先依次演示：内存数据结构存储、缓存、消息管道。
通过实例理解名词。

## 安装

Mac:
```bash
$ brew install redis
```

**澄清**

很多攻略给出的 Redis 安装方式是：

```bash
wget http://download.redis.io/releases/redis-stable.tar.gz
tar xzf redis-stable.tar.gz
cd redis-stable/
make
sudo make install
```
这是以前官网推荐的方式，理由是 brew / apt-get 安装的版本太老。

实测，当前 brew 安装的就是最新 stable 版 3.07，所以无需编译安装。

## 基本用法

#### 开启服务器

```bash
$ redis-server
```

如果要运行在后台，在命令后加一个 `&` ，即：`redis-server &`


打开另外一个终端，
运行命令行界面（Command Line Interface，简称 cli)，连接到 Server
```bash
$ redis-cli
127.0.0.1:6379> ping
PONG
```

发送 ping，回复 pong，则表示链接成功。

否则
```bash
127.0.0.1:6379> ping
Could not connect to Redis at 127.0.0.1:6379: Connection refused
```

#### Key-Value 存储

使用 GET / SET 命令，key 和 value 都是 string

```bash
127.0.0.1:6379> set name jackon
OK
127.0.0.1:6379> set gender male
OK
127.0.0.1:6379> get name
"jackon"
127.0.0.1:6379> get gender
"male"
127.0.0.1:6379> set age 16
OK
127.0.0.1:6379> get age
"16"
127.0.0.1:6379> get name
"jackon"
```

#### 常用命令 keys ／ flushdb / del

```bash
127.0.0.1:6379> keys *
1) "age"
2) "gender"
3) "name"
127.0.0.1:6379> del name
(integer) 1
127.0.0.1:6379> keys *
1) "age"
2) "gender"
127.0.0.1:6379> flushdb
OK
127.0.0.1:6379> keys *
(empty list or set)
```

#### 编程语言接入－－Python 为例

搭建基础的 Python 开发环境，参考[搭建 PYTHON 开发环境](http://jackon.me/posts/python-dev-env/)

安装 Python 的 redis 包：
```bash
$ pip install redis
Collecting redis
  Downloading redis-2.10.5-py2.py3-none-any.whl (60kB)
    100% |████████████████████████████████| 61kB 68kB/s
Installing collected packages: redis
Successfully installed redis-2.10.5
```

Python 代码

```python
# -*- Encoding: utf-8 -*-
import redis

r = redis.StrictRedis()
r2 = redis.StrictRedis(host='127.0.0.1', port=6379)

print 'connection 1: %s' % r
print 'connection 2: %s' % r2

r.set('name', 'jackon')
print 'name is %s' % r.get('name')
```

执行结果

```bash
$ python test.py
connection 1: StrictRedis<ConnectionPool<Connection<host=localhost,port=6379,db=0>>>
connection 2: StrictRedis<ConnectionPool<Connection<host=127.0.0.1,port=6379,db=0>>>
name is jackon
```

#### 复杂数据结构

- List: 列表(链表)
- Set: 集合
    与列表的区别是，集合内的元素不重复
- Sorted set 有序集合
    与 set 相似，每个元素对应一个 score(浮点数)，用于排序
- Hash 哈希表

Redis 命令虽然多，但都遵循一个很好的模式。

- SET 命令以 S 开始
- 有序集合以 H 开始
- 哈希表以 H 开始
- 列表，以 L(左)或 R(右) 开始，取决于操作方向。

偷个懒，用 python 批量插入一些数据。
当然，也可以在 redis-cli 里手动添加多个数据测试。

```python
# -*- Encoding: utf-8 -*-
import redis

r = redis.StrictRedis()

r.flushdb()

for i in range(3):
    r.sadd('total', i)
    r.lpush('seq', i)

for i in range(3):
    r.sadd('total', i)
    r.lpush('seq', i)

print '%s elements in set' % r.scard('total')  # card is short for cardinality
print '%s elements in seq' % r.llen('seq')  # len is short for length
```

执行结果：

```bash
$ python test2.py
3 elements in set
6 elements in seq
```

redis-cli 查看执行结果

```bash
127.0.0.1:6379> keys *
1) "total"
2) "seq"
127.0.0.1:6379> scard total
(integer) 3
127.0.0.1:6379> llen seq
(integer) 6
127.0.0.1:6379> sadd total 11 21
(integer) 2
127.0.0.1:6379> smembers total
1) "0"
2) "1"
3) "2"
4) "11"
5) "21"
127.0.0.1:6379> lrange seq 0 -1
1) "2"
2) "1"
3) "0"
4) "2"
5) "1"
6) "0"
127.0.0.1:6379> lpush seq 11
(integer) 7
127.0.0.1:6379> lrange seq 0 -1
1) "11"
2) "2"
3) "1"
4) "0"
5) "2"
6) "1"
7) "0"
127.0.0.1:6379> rpush seq 21
(integer) 8
127.0.0.1:6379> lrange seq 0 -1
1) "11"
2) "2"
3) "1"
4) "0"
5) "2"
6) "1"
7) "0"
8) "21"
```

#### 缓存与 TTL

基本的 Key-Value 存储 ＋“到期”功能

到期功能，
即 set 命令设置 key ＝ value 时，可以为 key 设置一个到期时间，比如 30秒 后。
到期后，Redis 自动删除这个键值对。其他的键值对不受影响。

到期功能，有助于避免总的键集无限增长。

基本用法演示：

```shell
27.0.0.1:6379> setex ice 10 "I'm melting..."
OK
127.0.0.1:6379> ttl ice
(integer) 8
127.0.0.1:6379> get ice
"I'm melting..."
127.0.0.1:6379> exists ice
(integer) 1
127.0.0.1:6379> ttl ice
(integer) -2
127.0.0.1:6379> exists ice
(integer) 0
127.0.0.1:6379> get ice
(nil)
```

重新设置相同的值，会覆盖之前的数据，TTL 重新开始倒计时。
```bash
127.0.0.1:6379> setex ice 10 "I'm melting..."
OK
127.0.0.1:6379> ttl ice
(integer) 8
127.0.0.1:6379> setex ice 10 "I'm melting..."
OK
127.0.0.1:6379> ttl ice
(integer) 9
```


**黑科技：当 Redis 的 TTL 遇到了爬虫**

```python
# -*- Encoding: utf-8 -*-
import redis
import time

r = redis.StrictRedis()
r.flushdb()


def req():
    time.sleep(1)
    print 'requesting jackon.me...'


lock_name = 'http-lock'
THRESHOLD = 3

while True:
    t = r.ttl(lock_name)
    if t > 0:
        print 'sleep %s seconds' % t
        time.sleep(t)

    r.setex(lock_name, THRESHOLD, 'locking')
    req()
```

一旦爬虫被封，进入 redis，setex 一下 'http-lock' 的 TTL。
爬虫自动进入休眠状态。


#### 发布 － 订阅

如果简单，以至于任何文字都是多余的。

看图
![redis-sub-pub](https://raw.githubusercontent.com/JackonYang/IOut.me/master/images/mac-etc/redis-sub-pub.png)