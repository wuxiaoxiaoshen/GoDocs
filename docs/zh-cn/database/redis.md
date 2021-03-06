# redis


### 1. 基本的数据类型

- string
- list
- sort
- zsort
- hash

针对各种数据类型的基本操作：

- C
- U
- R
- D

### 2. 典型应用场景

- TOP N


### 3. Tips

批量删除 key
```
redis-cli keys "*idiom:hash*" | xargs redis-cli del

```

docker 中如何删除？

- 到容器内
- 到 执行上述的命令

### 4. 占用内存查看

 ```
>> info memory
used_memory:27408240
used_memory_human:26.14M
 ```

 ### 5.  查看数据库

 ```
>> info keysapce
# Keyspace
db0:keys=44069,expires=0,avg_ttl=0


>> config get databases
databases
16

 ```

### 5. 如何选择数据库

```
c, err := redis.Dial("tcp", ":6379", redis.DialDatabase(0))
接收一系列参数，其中可以选择选项

```

```
>> redis-cli --raw -n 1

```

### 6. BitMap

```
>> setbit name:1 4 1 // name 的第4位为1

>> getbit name:1 4 // name 的第4位

>> bitcount name:1

```

>  统计计数一般都选择的是 bit

### 7. 发布订阅

```
>> SUBSCRIBE channalname

>> PUBLISH channaalname

1对多，缺点：重新订阅不能得到全部的数据

```

### 8. 启动停止

```
>> redis-server // 启动服务
>> redis-cli shutdown // 停止服务

```
