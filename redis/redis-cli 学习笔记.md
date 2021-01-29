## redis-cli 学习笔记



### 链接 redis

redis-cli -h host -p port -a password

ping 返回PONG表示链接正常



### key 操作

exists 确认key是否存在

del key 删除指定key

type key 返回key对应值的类型

keys * 返回所有的key

randomkey key 随机返回一个key

keyrename oldkey newkey 重命名key

dbsize 返回当前key的数目

expire：设定一个key的有效期

ttl 获得一个key的有效期

move key dbindex 移动当前数据库中的key到dbindex数据库

flushdb 删除当前选择数据库中的所有key

flushall 删除所有数据库中的所有key



### string 操作

set key value 设置一个键值对

get key 获取 获取指定键对值

getset key value 将key的值的值设为value并返回原来的值

incr key 递增数字

decr key 递减数字

incrby key increment 增加指定的整数

decrby key increment 减少指定的整数

incrbyfloat key increment 增加指定浮点数 （v2.6+）

append key value 向尾部追加值

substr key start end 返回指定key值的子串

strlen key 返回字符串长度

mget key1 key2 key3 … 同时获取多个key

mset key1 value1 key2 value2 … 同时设置多个key

setnx key value 当key不存在时，将key的值设为value

setex key seconds value 将key的值的值设为value并且设置有效期秒数，当key存在时覆盖原值



### list 操作

lpush key value value2 … 左边入列

rpush key value value2 … 右边入列

lpop key 左边出列

rpop key 右边出列

llen key 返回列长度

lrange key start stop 返回start到stop之间的所有元素，索引从0开始，支持负数，表示从右边开始计算

lrem key count value 删除列表中 count个值为value的元素，返回实际删除的元素个数

lindex key index 获取列表指定索引的值

lset key index value 设置列表指定索引的值

ltrim key start end 删除指定索引范围之外的所有元素

linsert key [before,after] value1 value2 在列表值为value1之前或之后插入value2



### **set 操作**

sadd key member1 member2 … 向集合中增加一个或多个元素 (member不能重复)

srem key member 删除名称为key的set中的元素member

spop key 移除并返回集合中的一个随机元素

smove srckey dstkey member 移到集合元素

scard key 返回名称为key的set的基数

sismember key member 返回member是否是名称为key的set的元素

sinter key1, key2 … 求交集

sinterstore dstkey keys 求交集并将交集保存到dstkey的集合

sunion key1 keys 求并集

sunionstore(dstkey, (keys)) ：求并集并将并集保存到dstkey的集合

sdiff key1 keys 求差集

sdiffstore dstkey keys 求差集并将差集保存到dstkey的集合

smembers key 返回名称为key的set的所有元素

srandmember key ：返回集合中的一个随机元素



###  **Hash 操作**

hset key field value 向名称为key的hash中添加元素field

hget key field 返回名称为key的hash中field对应的value

hmget key fields 返回名称为key的hash中field i对应的value

hmset key fields 向名称为key的hash中添加元素field

hincrby key field integer 将名称为key的hash中field的value增加integer

hexists key field 名称为key的hash中是否存在键为field的域

hdel key field 删除名称为key的hash中键为field的域

hlen key 返回名称为key的hash中元素个数

hkeys key 返回名称为key的hash中所有键

hvals key 返回名称为key的hash中所有键对应的value

hgetall key 返回名称为key的hash中所有的键（field）及其对应的value

