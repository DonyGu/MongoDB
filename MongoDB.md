# 数据类型
+ 字符串
+ 整型
+ 布尔值
+ 浮点型
+ 数组类型
+ 时间类型
+ 文档类型
+ 空值NULL
+ 字符串（symbol通常表示特殊字符）
+ 时间戳
+ ObjectID
+ 二进制
+ 代码js
+ 正则表达式

# 概念
|mysql|mongoDB|含义|
|--|--|--|
|database|database|数据库|
|table|collection|表/集合|
|column|field|字段/域|
|row|document|记录/文档|
|index|index|索引|

# 基础操作
+ 进入mongo shell: `mongo`
+ 退出mongo shell：`quit()`
+ 创建数据库： `use databasename`
    + use实际的的功能表示你选择使用哪个数据库，如果选择一个不存在的数据库则向这个数据库插入数据时，数据库会自动创建。
+ 查看当前数据库系统中的数据库：`show dbs`
+ 备份数据库：`mongodump -h dbhost -d dbname -o dbdir`
    + e.g.:`mongodump -h 127.0.0.1 -d stu -o student`
    + 将本机stu数据库备份到当前目录下的student文件夹
+ 恢复数据库：`mongorestore -h <hostname>:<port> -d dbname <path>`
    + e.g.：`mongorestore -h 127.0.0.1:27017 -d test student/stu`
+ 删除数据库：`db.dropDatabase`
+ 数据库检测：`mongostat`

|字段|含义|
|--|--|
|inserts|当前mongodb插入数量|
|query|当前mongodb的查询数量，数量以每秒为单位
|update|当前mongodb的更新数量
|delete|当前mongodb的删除数量
|getmore|在进行mongodb查询时，每次并不是返回所有的数据，比如要一次查询一百万条，每次只会返回一定量的数据，当每次find的时候，getmore用来获取以后的数据
|command|执行命令的数量
|flushes|在mongodb写入数据，查询数据时，我们看到的数据是在内存中，实际上并不是在内存中，有些是在硬盘上的，每个一段时间，mongodb会把内存数据刷到硬盘上，flushes就是看mongodb隔多久往磁盘上刷一次
|mapped,vsize,res|mongodb所占据到磁盘空间大小和申请的内存大小
|faults|如果数据没有加塞到内存中，需要到硬盘上读取
|locked|锁的情况
|ids miss|表明当前查询没有使用索引的情况
|qrw|在写入或读取数据时，并不是来个请求就处理，而是放到队列中，如果请求比较多，或者mongodb处理比较慢，这样qr,qw比较高，一般到qr,qw比较高时，比如几百上千，mongodb的性能会出现明显的下降
|arw|当前活跃的客户端的数目
|netIn,netOut|mongodb使用网卡的输入流量
|conn|连接到mongodb到连接数量

+ 检测每个数据库的读写时长：`mongotop`

|ns|total|read|write|
|--|--|--|--|
|数据表|总时长|读时长|写时长|
# 数据库的命名规则
1. 原则上是满足以下几条的任意UTF-8格式的字符串
2. 不能是''字符（空字符）
3. 不能含有空格' '，点'.'，'/','\','\0'
4. 习惯上全部小写
5. 不应超过64字节
6. 不能使用admin，local，config这三个名字

# 系统数据库
+ admin：存储用户权限
+ local： 不会复制，只能用于本机操作
+ config： 分片处理时存储分片信息
+ db: 全局变量，当前使用的数据库，默认test