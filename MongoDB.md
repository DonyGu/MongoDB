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



