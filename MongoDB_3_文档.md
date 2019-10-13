# 文档
## 基础概念
+ MongoDB的文档等同于SQL的记录
+ 在mongodb中数据的组建形式
+ 由键值组成
+ mongodb中数据文档为bson格式
## 文档中键的命名规则
1. utf-8格式的字符串
2. 不能由'\0'，不能为空
3. 以_开头的很多事保留的键，，所以一般不用_开头
+ 注意
    1.  文档中的键值对是有序的
    2. 文档中的值指的就是文档支持的数据类型
    3. mongodb中区分大小写
## 支持类型
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

## 集合设计原则
1. 同一类文档存在一个集合中
2. 集合中尽量存储域和文档格式相近的文档
3. 集合中可以存在文档数据的差异

## 插入文档
+ 单文档插入
    + `db.collection_name.insert()`
+ 插入多条文档
    + `db.collection_name.insert([{},{}])`
+ save插入数据
    + `db.collection_name.save()`
        + 如果不添加_id域的时候，同insert
        + 如果添加_id域，该域值如果不存在则会添加，若存在会修改原有数据
        + save不能够插入多条文档

## 查找
+ find()
    + `db.collection_name.find()`-->`select * from tableName`
    + 功能：查找所有符合筛选要求的文档
    + 参数：
        + query：筛选条件 相当于where子句
            1. 以键值对的方式确定查找条件。
            2. 如果不写这个参数则表示查找所有文档。
            3. 
        + field：展示的域
            1. 以键值对的形式给每个域赋值表示是否要显示该域。
                + 0 表示 不展示该域
                + 1 表示 展示该域
            2.  如果给域设置为0，则其它域自动为1，如果给某个域设置为1，其他自动为0，两者不能混用。
            3. _id比较特殊，默认为1，如果不想显示则设置为0。_id为0时,其他值是可以为1的。
            4. 如果不写该参数，则表示全部显示。
    + 返回值：返回所有的符合要求的文档
    + e.g. `db.class.find({age:22},{_id:0，name:1})`
+ findOne
    + `db.collection_name.findOne()`
    + 功能：查找符合条件的第一条文档
    + 参数：同find
    + 返回值：返回查找到的文档

## 删除文档
+ remove()
    + `db.collection_name.remove(query,justOne)`
    + 功能：删除文档
    + 参数：
        + query：同find
        + justOne:bool值，是否删除第一条匹配到的文档，默认false。

## 更新文档
+ update()
    + `db.collection_name.update(query,update,upsert,multi)`
    + 功能：更新一个文档数据
    + 参数：
        + query：定位要更新的数据，与find用法相同
        + update: 将数据更新为什么，相当于set，需要配合修改器操作符来使用
        + upsert: bool值，默认false，表示当定位的文档不存在则无法修改。如果设置为true，表示如果定位的文档不存在则插入这条文档。
        + multi：bool值，默认为false，如果query匹配的文档有多条只修改第一条。如果设置为true，则修改所有匹配到的文档。
        + e.g.: `db.class.update({name:'a'},{$set{age:19}})`
