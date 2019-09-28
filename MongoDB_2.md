# 集合的创建和删除
+ 创建集合
    1. `db.createCollextion()`
    2. 当向一个集合中插入一条文档，如果这个集合不存在，则会自动创建`db.collection_name.insert()`
+ 集合的命名规则
    1. 不能是空字符串
    2. 不能含有'\0'
    3. 不能以system开头，这是系统集合的保留前缀
    4. 集合不要和保留字重名不要包含$
+ 查看数据库中的集合

    `show tables`或`show collections`
+ 删除集合

     `db.collection_name.drop()`
# 文档
+ 在mongodb中数据的组建形式
+ 由键值组成
+ mongodb中数据文档为bson格式
+ 文档中键的命名规则
    1. utf-8格式的字符串
    2. 不能由'\0'，不能为空
    3. 以_开头的很多事保留的键，，所以一般不用_开头

    + 注意
        1.  文档中的键值对是有序的
        2. 文档中的值指的就是文档支持的数据类型
        3. mongodb中区分大小写
+ 支持类型

|类型|注释|
|--|--|
|整型|整数，32位整型|
|布尔|True，False|
|浮点型|存储小数|
|Arrays|列表数组|
|Timestamp|时间戳|
|Date|时间日期|
|Object|内部文档|
|Null|空值|
|Symbol|特殊字符串|
|Binary data|二进制数据|
|code|代码|
|regax|正则表达式|
|ObjectId|ObjectId字符串|
+ 集合设计原则
1. 同一类文档存在一个集合中
2. 集合中尽量存储域和文档格式相近的文档
3. 集合中可以存在文档数据的差异



